# Python Installation for Projects

* ** Install [pyenv](https://github.com/yyuu/pyenv) to maintain different versions of python**
    * [tutorial](http://amaral-lab.org/resources/guides/pyenv-tutorial) and [here](http://fgimian.github.io/blog/2014/04/20/better-python-version-and-environment-management-with-pyenv/) 
    * instal *pyenv-virtualenv* using 
        * git clone https://github.com/yyuu/pyenv-virtualenv.git ~/.pyenv/plugins/pyenv-virtualenv
    * install a few versions of python such as 
        * pyenv install 2.7.10
            pyenv install 2.7.8
            pyenv install 3.4.0 
    * set one of them as you global python
        * pyenv global 2.7.10 
* **when creating a project**
    * first create a virtualenv with the version of python that you want to use (make sure the name of the virtual env includes the version of python)
        * pyenv virtualenv 2.7.10 venv_2.7.10

    * go to project directory and set it up to use this virtualenv
        * cd projectdir
            pyenv local venv_2.7.10

    * this creates a *.python-version* file in your project directory. Commit it to the repository
    * install all packages that your project needs with *pip install <package_name>*. Then freeze pip with
        * pip freeze > requirements.txt 

    * commit the requirements.txt file to the repository
* **When replicating a project**
    * open the *.python-version *file and look at the virtualenv name in it
    * create a virtualenv with the same name with the version of python thats in the name. For example if the name is *venv_3.4.0* you will first install python 3.4.0 and then use it to create this virtualenv
        * pyenv install 3.4.0
            pyenv virtualenv 3.4.0 venv_3.4.0

    * then install all the pip requirements
        * pip install -r requirements.txt

    *   you should now have the intended environment. every time you cd into the project directory, pyenv automatically changes the virtualenv to *venv_3.4.0 * and all pip install happen there.
* Installing CV2
    * [find package destination](http://stackoverflow.com/questions/122327/how-do-i-find-the-location-of-my-python-site-packages-directory)
    * [make symlink to compiled cv2.so](https://jjyap.wordpress.com/2014/05/24/installing-opencv-2-4-9-on-mac-osx-with-python-support/)
