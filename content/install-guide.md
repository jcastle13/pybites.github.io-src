Title: How to get PyBites up and running on your machine
Date: 2016-12-20 10:40
Category: Tools
Tags: pelican, publishing, github, pip, virtualenv, git
Slug: install-me
Authors: Pybites
Summary: This is a short post for Julian to get this Pelican blog up and running on his system.
cover: images/featured/pb-article.png

This is also a useful ref for future collaborators ...

We're open source right? ;)

## Pybites install guide

	# we have a src, output and theme (Flex) repo, use --recursive to get all
	# If using SSH then run the following command:
	$ git clone --recursive git@github.com:pybites/pybites.github.io-src pybites
	# If using HTTPS then run the following command:
	$ git clone --recursive https://github.com/pybites/pybites.github.io-src pybites
	
	# Then change into the directory
    $ cd pybites

	# set up env and install dependencies
    $ virtualenv venv (might need: virtualenv -p python3 venv)
    $ source venv/bin/activate
    $ pip install -r requirements.txt

	# add some content
    $ cd content
    $ vi new-blog-post.md ; wq!

	# check changes on localhost
	$ cd ..
    $ make html && make serve 

	# push this new content to the parent -src repo
    $ git add . 
	$ git commit -m "my new blog post"
	$ git push

	# push the static blog change to the child -io repo
	# wait: this is a duplicate step, I don't like duplication!
	# ...

As we have 2 repos: -src for code, -io for generated static content, ideally we want to automate the publishing to -io, so we can just focus on the main repo (-src). 

Here is where [git hooks](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks) come into play. cd into .git/hooks and add below script, name it "pre-push", update your WORKING_DIR and chmod 755 it ...

UPDATE: we abondonded this hook, because it led to some conflicts / unnecessary work, not worth automating this step. We push manually to -src / -io these days. 
