When you want to install a package in Zync, Zync will first create a 1 time connections to 5 trusted repositeries added by Zync maintainers.
Then it will create an isolated enviroment and install that package from 5 repositeries through a fully encrypted HTTPS connection. 
then it will cut connection with repos.
(also it will install the same version of the package from repos)
(so there will be 5 editions of the same package from repos). 
(if a repositerie does not have the latest version it will add UNTRUSTED tag to repo. which Zync cannot use repos with UNTRUSTED tags)
then it will compare the these packages comes from the repos using a merkel tree.
if even there is a significant difference beetween any editions it will cancel the installion and throws an error.
when it becames sure everything about this packages are EXACTLY same,
it will select an edition of the package from the most trusted repo in a separate isolated enviroment and delete the other editions(Every repo has a trust level from 1 to 5)

Package comparaison:
Every package has two SHA256 fingerprints
one of these fingerprints are only can be activated by the creator of the app
one of these fingerpirnts is produced by the maintainer of the package 
when Zync gets packages on isolated enviroment it will compare metadata and fingerprints of the each edition of the package using a merkel tree
