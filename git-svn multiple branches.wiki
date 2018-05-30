
[core]
	repositoryformatversion = 0
	filemode = true
	bare = false
	logallrefupdates = true
[svn-remote "svn"]
	url = https://svn.keepthinking.net/wkcd
	fetch = branches/crm_integration:refs/remotes/origin/crm
	fetch = branches/website_enhancement_2018:refs/remotes/origin/2018
  
  
git svn fetch
git checkout -b local-newBranch remotes/origin/branch
