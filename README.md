# CI_CD_PIPELINE
Steps to pipeline job for Java installation 
1. Create a git repository
2. install the jenkins , ansible plugin must be installed
3.  configure the github repository with Jenkins
4. Create a pipeline job with option pipeline script from SCM
5. create playbook  for check version , update version and install version
ansible-playbook javacheck.yml --extra-vars "version=1.8.0_232"
