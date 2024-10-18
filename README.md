# A-vmimport subprocess

def install_ansible():
    print("Installing Ansible...")
    subprocess.check_call(['pip', 'install', 'ansible'])

def setup_vm():
    print("Setting up the virtual machine environment...")
    ansible_playbook = '''
    - hosts: localhost
      tasks:
        - name: Ensure VM is up-to-date
          apt:
            update_cache: yes
            name: "*"
            state: latest
    '''
    with open('setup.yml', 'w') as file:
        file.write(ansible_playbook)
    subprocess.check_call(['ansible-playbook', 'setup.yml'])

if __name__ == '__main__':
    install_ansible()
    setup_vm()
    
