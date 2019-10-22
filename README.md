# fix_that_dirty_bug

## required

You'll need : 

- a token (file or cli)
- a git base url (file or cli)

The files must be located in 

```
$ pwd
/home/$USER/.config/ftdb/
```

### token

Generate a token from gitlab with the API scope ([doc](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html))

Pass the token via the cli param `-t 'token'` of create a file with the token inside :

```bash
$ cat .config/ftdb/.git_token
SECRET_TOKEN
```

### base url 

The base url should be the http dns of your git server. Pass the value via the cli param `-u 'http://git.mycomany.org'` or via a file : 

```bash
$ cat .config/ftdb/.base_url
http://git.mycomany.org
```

## usag

```bash
14:47:46 ❯ fix_that_dirty_bug -h
usage:

    fix_that_dirty_bug -n 'issue name' -b 'branch name' -p 'project name' -a 'assignee' [ -d 'issue description' ]  [ -t 'git token' | -T '/token/path' ] [ -u 'base url' | -B '/base/url/path' ]   [ -U|-P ] [ -l (0..3)]

    Required params :
        -n : issue name
        -b : branch name (format: master-[issue id]-[cli val])
        -p : project name
        -a : user assigned to the issue and MR

    Optional params :
        -d : issue description
        -t : git token
        -T : git token file path
             Default : [/home/master/.config/ftdb/.git_token]

        -u : base url to query the git API
        -B : base url file path
             Default : [/home/master/.config/ftdb/.base_url]

        -U : force re-create and display the user list
        -P : force re-create and display the project list

        -l : log level (0=error,1=info,2=warn,3=debug).
             Default : [2]

Create an issue, then push the work to a automatic branch, create an MR from the branch which reference the newly created issue.

Return value :

       -2 : no git url provided
       -1 : no git token provided
       0  : 
       1  : wrong cli param
       2  : not in a git repository
       3  : missing curl binary
       4  : error while creating the issue
       5  : error while creating the merge request
       6  : can't fetch the project list
       7  : can't fetch the users list
       8  : can't fetch project ID
       9  : can't fetch git user ID
       10 : can't fetch the created issue ID
```

Explain what it is

Explain how it work

Explain how to use it

Link gitlab token gen

Quick use
