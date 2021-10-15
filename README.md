# Sample playbook for Moodle installation

To run this playbook, you either need to use molecule to test locally or to
build an inventory based your infrastructure.

## Create a new encrypted password

    ansible-vault encrypt_string '12345ABCD' --name 'dbpass'

## See the password that have been encrypted

    ansible -l <servername> -m debug -a "var=mysql_users" all

## Apply changes

    ansible-playbook -l <servername> playbook.yml

## Just update code

    ansible-playbook -l moodle1 webserver-tools.yml --tags "task-updatecode"

## Run a command on all hosts

    ansible  all -m shell -a 'hostname'
    ansible  all   -a "/sbin/reboot" --become
