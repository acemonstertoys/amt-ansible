
# Install Postgres on AMT Rocket
ansible-playbook -i amt_rocket.ini amt_infra.yml --ask-sudo-pass


# Change the user
	Goto defaults/main.yml  update  
	
	user_to_use: "Your UserName"


## Playing on a real cloud server

If you already have a Cloud Hosting account and want to test this playbook there, go ahead and just edit the hosts/production file with your hosts information and edit the group_vars/producrion.

Then, all you have to do is run the following command:

    ansible-playbook -i hosts/{{ environment }} site.yml --ask-pass --ask-sudo-pass
    
	# For Dev
    ansible-playbook -i hosts/dev site.yml --ask-pass --ask-become-pass
    
    # For staging
    ansible-playbook -i hosts/staging site.yml --ask-pass --ask-become-pass
    
    # To see actual commands debugging
    ansible-playbook -i hosts/dev site.yml --ask-pass --ask-become-pass -vvvv
    
PS: Some Cloud providers' VPSs come with iptables firewall enabled blocking all the traffic. In this case you will have to set up some rules in order to test this playbook. If you don't mind opening all ports, you can flush the firewall rules by running the following command: