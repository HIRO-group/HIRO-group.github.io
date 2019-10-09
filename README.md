# Making Pull Requests

Joining the group? Need to make a pull request to add your details to the "People" page?

First, clone the repository onto your computer. Using Terminal, navigate to the location you would like the repository to live, and run the following commands.

```
git clone https://github.com/arpg/arpg.github.io.git
cd arpg.github.io
```

If you have SSH keys set up with GitHub, you can run the following instead.

```
git clone https://github.com/arpg/arpg.github.io
cd arpg.github.io
```

Make your edits in a new Git branch. The following command will simultaneously create and switch to your new branch. Replace `<branch-name>` with your desired branch name, e.g. `add-hackman`.

```
git checkout -b <branch-name>
```

Once you've made the changes you want, make the commit! Include a commit message with the `-m` flag. An example commit message is given below.

```
git commit -m "Add <name> to people page"
```

You're finally ready to push your changes to your very own remote branch! Run the following command with the same branch name you used above.

```
git push origin <branch-name>
```

You're almost done! Go back to the GitHub repository page, and there should be a button near the top of the page to open a new pull request.

If you'd like, after your pull request has been merged, you can delete the branch from your local repository.

```
git branch -d <branch-name>
```

# Adding to People Page

To add your name and photo to the list of lab members, add your details to the file in at `./_data/people.yml`. Be sure to follow the existing format or you'll break things. 

```
 - name: 
   role: <faculty/postdoc/manager/phd/grad/undergrad/alumni>
   url: <url to your personal webpage>
   office: 
   phone: 
   email: 
   pic: <looks in img/people>
```

Additional fields for alumni

```
   dates: 
   thesis: 
   advisor: 
   now: 
```

Also be sure to add your photo to `./img/people/`. The picture needs to be square, and preferably not bigger than 400x400 pixels.

To save your changes, you need to use the `git add` command to tell Git to include your updates in the next commit. In the root directory of the repository, run the following commands (replacing `<image-name>` with the name of your photo).

```
git add ./_data/people.yml
git add ./img/people/<image-name>
```

# Adding to Research/Overview Page

To add or update the information on a research project, edit the file `./_data/research.yml

```
  - project: 
   img: /img/
   blurb: ""
   webpage:
   publications:
     - title: 
       authors:
       date: 
       venue: 
       url:
   funding:
     - 
```

Publications and funding both can be lists. YAML is fussy about certain characters for example colons (:), so if you are unsure whether your character are safe, surround with quotes (").

# Adding a new publication

To add or update the information on a publication project, edit the file `./_data/publications.yml

```
 - title: 
   authors: 
   year: 
   venue: 
   pdf: 
```

If you need to upload your paper locally, we recommend putting pdfs in the `./papers/` directory.

# Adding a news item

Add a markdown file to the `./_posts/news/` directory. The name should be in the format `yyyy-mm-dd-title-with-hyphens-instead-of-spaces.md`. The full text of the file will be used as the news post. 

# Adding a stand-alone research page

Add a markdown file to the home directory with the following header

```
type: article
title: <Your Page Title>
```

The article flag will format your page nicely. Without the flag, there will be no navigation bar, css, etc.

To add your page to the navigation bar, you'll need to edit `./_includes/header.html`   

