ansible-role-jenkins_as_docker
=========

This role installs jenkins on a Docker conatiner based on the official jenkins image in docker hub

Requirements
------------

Have docker-ce already installed on the host

Role Variables
--------------

"jenkins_home_dir_host" -- The path to a local mount on the host mapped to the jenkins directory in the container
"jenkins_home_dir_container" -- The path to the jenkins home directory in the container

"jenkins_user_id" -- Set to 1000 since we are mapping the volume to a mount bind
"jenkins_group_id" -- Set to 1000

"jenkins_image_name" -- Official IMage name of Jenkins in Docker Hub
"jenkins_image_tag" -- The tag name of the image you want to use

"jenkins_instance_name" -- Recognizable name of the jenkins container instance
"docker_host_port" -- The host port you want mapped to the container port 8080

"jenkins_footer_url" -- Custom footer definition passed as JAVA_OPTS


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - arjun-kanniah/ansible-role-jenkins_as_docker

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
