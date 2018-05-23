# Migrate from Subversion to Git - Authors Lookup

During the [Migration from Subversion to Git](https://www.atlassian.com/git/tutorials/svn-to-git-prepping-your-team-migration) there is a file created `authors.txt`.
This file contains the author ID's as used in Subversion commits. The ID's are extracted per Subversion repository, based on the commits in the Subversion repository.
Apart from the Subversion ID's it generates a kind of Git ID's.

In the [Prepare step](https://www.atlassian.com/git/tutorials/migrating-prepare) there is this command which generates the file `authors`, as shown below.

	java  -jar svn-migration-scripts.jar  authors  http://subversion.company.org/svn/project/hello-world/  > authors.txt

The Subversion repository could contain the following `authors.txt`:

	in063dij = in063dij <in063dij@mycompany.com>
	in083hof = in083hof <in083hof@mycompany.com>
	in386won = in386won <in386won@mycompany.com>
	in521gha = in521gha <in521gha@mycompany.com>
	in588kow = in588kow <in588kow@mycompany.com>
	jenkins = jenkins <jenkins@mycompany.com>


This generated file `authors.txt` should actually contain the _full name_ and _e-mail address_ of these commiters, as shown below.

	in063dij = Jeroen van Dijk <jeroen.vandijk@company.org>
	in083hof = Anneke Hofstra <anneke.hofstra@company.org>
	in386won = Dennis Wong <dennis.wong@company.org>
	in521gha = Suha Ghaghos <suha.ghaghos@company.org>
	in588kow = Greg Kowal <greg.kowal@company.org>
	jenkins = Jenkins <jenkins@company.org>


## The Idea

Lookup author ID's through a RestFul Web Service, get each authors _full name_ and _e-mail address_.


## To Do List

- [ ] Generate git user configuration based on LDAP (Windows) user ID  
      - user.name  
      - user.email  

	git config --global user.name "Hugh Jass"
	git config --global user.email "hugh.jass@company.org"  

- [ ] Upload initial authors file to web service - return generated file.
- [ ] Web Interface - post authors, generate new page containing the lookup authors.
- [ ] Add support for users that are no longer in LDAP  
      Local h2sql or similar database?


