## Virtual Environment

Have you ever heard of `virtualenv`? The chances are that if you are a beginner then you might not have heard about it but if you are a seasoned programmer than it's a vital part of your toolset. So what `virtualenv` really is? `Virtualenv` is a tool which allows us to make isolated python environments. Imagine you have an application that needs version 2 of a LibraryBar, but another application requires version 3. How can you use and develop both these applications? 

If you install everything into `/usr/lib/python2.7/site-packages` (or whatever your platform's standard location is), it's easy to end up in a situation where you unintentionally upgrade a package that shouldn't be upgraded. In another case just imagine that you have an application which is fully developed and you do not want to make any change to the libraries it is using but at the same time you start developing another application which requires the updated versions of those libraries. What will you do? It is where `virtualenv` comes into play. It creates isolated environments for you python application and allows you to install Python libraries in that isolated environment instead of installing them globally. 

In order to install it just type this command in the shell:

```python
$ pip install virtualenv
```

Now i am going to list some of it's commands. The most important ones are:

- ```$ virtualenv myproject```
- ```$ source bin/activate```

This first one makes an isolated virtualenv environment in the `myproject` folder and the second command activates that isolated environment. While running the first command you have to make a decision. 

```python
$ virtualenv --no-site-packages mycoolproject
```

Now you can install any library without disturbing the global libraries or the libraries of the other environments. You can turn off the `env` by typing:

```python
$ deactivate
```

This was just a short intro to virtualenv. There's a lot more to it. For further study i recommend [this link.](http://docs.python-guide.org/en/latest/dev/virtualenvs.html) It will remove all of your confusions about virtualenv. 