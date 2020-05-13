# Python Stack 

This python stack is based in the this one https://github.com/appsody/stacks/tree/master/incubator/python-flask

This one modifies the Dockerfiles to fix the user permissions and add `oc` and `htpasswd` commands. This is how I build it:

1. Create the base template to modify over:

```console 
foo@bar:~$ appsody stack create python-stack --copy incubator/python-flask
```
2. Modify the Docker files to change the python base image with the one that contains the `oc` and `htpasswd` commands: 
- [image/project/Dockerfile](https://github.com/chechuironman/kabanero-python-stack/blob/master/image/project/Dockerfile) 
- [image/Dockerfile-stack](https://github.com/chechuironman/kabanero-python-stack/blob/master/image/Dockerfile-stack)
3. Modify the [stack.yaml](https://github.com/chechuironman/kabanero-python-stack/blob/master/stack.yaml) file with the info of the new stack.
4. Package the stack:

```console 
foo@bar:~$ appsody stack package
```

5. Validate the stack:

```console 
foo@bar:~$ stack validate
```

6. Add the stack to the stack hub:

```console 
foo@bar:~$ appsody stack add-to-repo chechu-repo --release-url https://github.com/chechuironman/kabanero-stacks/releases/latest/download
```

In my Kabanero stack hub you can see instructions on how to expose the files to your OpenShift instance:

[https://github.com/chechuironman/kabanero-stacks](https://github.com/chechuironman/kabanero-stacks)
