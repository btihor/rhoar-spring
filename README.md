# rhoar-spring
## …or create a new repository on the command line

```
echo "# rhoar-spring" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/btihor/rhoar-spring.git
git push -u origin master
```
## …or push an existing repository from the command line
```
git remote add origin https://github.com/btihor/rhoar-spring.git
git push -u origin master
```
## …or import code from another repository

You can initialize this repository with code from a Subversion, Mercurial, or TFS project.


---
Image Stream 
```
oc login -u system:admin
oc create -n openshift -f https://raw.githubusercontent.com/jboss-openshift/application-templates/ose-v1.4.14/openjdk/openjdk18-image-stream.json

oc create -n openshift -f https://raw.githubusercontent.com/jboss-openshift/application-templates/ose-v1.4.14/openjdk/openjdk18-image-stream.json

oc create -n openshift -f https://raw.githubusercontent.com/jboss-openshift/application-templates/ose-v1.4.14/webserver/jws31-tomcat8-image-stream.json

```
---

# CI/CD Setup in OCP 3.11

## Create Projects
oc new-project dev --display-name="Tasks - Dev"
oc new-project stage --display-name="Tasks - Stage"
oc new-project cicd --display-name="CI/CD"

## Grant Jenkins Access to Projects
oc policy add-role-to-group edit system:serviceaccounts:cicd -n dev
oc policy add-role-to-group edit system:serviceaccounts:cicd -n stage




