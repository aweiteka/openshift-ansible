# Hacking on this Ansible Role

## Development Environment

1. Stand up OpenShift

         oc cluster up
1. Login

         oc login -u system:admin
1. Run installer from the base of the openshift-ansible repo

        docker run --rm -u root \
               --net=host \
               -v `pwd`/roles/openshift_prometheus_operator/hack/inventory:/tmp/inventory:z \
               -v $HOME/.kube/config:/etc/origin/master/admin.kubeconfig:z \
               -e KUBECONFIG=/etc/origin/master/admin.kubeconfig \
               -e INVENTORY_FILE=/tmp/inventory \
               -e PLAYBOOK_FILE=roles/openshift_prometheus_operator/operator.yml \
               -e OPTS="-vv" -it -v `pwd`:/usr/share/ansible/openshift-ansible:z \
               openshift/origin-ansible
1. Add developer user to openshift-metrics project

        oc policy add-role-to-user admin developer -n openshift-monitoring

### Issues

* If redeploying sometimes the openshift configuration needs to be wiped, then redeploy from step 1.

        sudo rm -rf /var/lib/origin/openshift.local.config

