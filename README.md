# Using WordPress with GitHub: A step-by-step guide to get up and running
As you may know, we’re big fans of WordPress and use the open-source workhorse any chance we can. But let’s face it—keeping your production site in line with your local testing site can become a nightmare if you don’t have the proper set up. Today we’re going to show you how 45royale builds and tests a WordPress site on local servers and then pushes those updates to a live production server.

One quick note before we get started: We’re going to assume that you have a local environment set up on your machine. We’ve been using MAMP for years as it provides an all in one solution for Apache, PHP and MySQL on a Mac OS environment. If you’re new to local development, check out this article to get up to speed on downloading and setting up MAMP. Have MAMP installed? Great, here’s what’s next:

## 1. Download WordPress
If you haven’t already downloaded WordPress after installing MAMP, go ahead and grab it now. Place it in your .htdocs folder so it’s ready for the next step.

## 2. Log in to GitHub
Log in to Github and create a repository for your new theme. Once you do, you’ll be able to get a clone URL for the repository (see below) ↓.

## 3. Clone your GitHub repository
Clone your new Github repository (we’re using the GitHub app for Mac) onto your local machine in the wp-content/themes folder where you installed WordPress. The result should leave you with a folder called wp-content/themes/theme_repo_name.

## 4. Copy and paste your files
Copy and paste all of the files from one of the default WordPress themes into your theme_repo_name folder (we’re using the twentyseventeen theme). If you have an alternative or existing theme you want to use, feel free to copy those over instead of one of the default theme(s).

## 5. Activate the theme
Log in to WordPress on your local server and activate the new theme.

## 6. Commit and push your files to GitHub
Git commit and push all of the new files in the working copy of your local repository to your remote GitHub repository.


## 7. Install WordPress on your remote server
This should be self-explanatory, just download and install WordPress on a remote web server. We use Digital Ocean for all of our sites — we highly recommend them.

## 8. Clone your repo via Terminal
Using the command line on your remote server, clone your repository into the wp-content/themes folder on the remote server. Ex: git clone https://github.com/mattdowney/test-repo.git. It will then prompt you to enter in your GitHub username and password before cloning.

## 9. Activate the new theme
Log in to WordPress on the remote web server and activate the new theme.

## 10. Make changes to your local theme
Make changes to the theme on your local server (we like using Sublime Text) then commit and push all of the changes to the remote repository.

## 11. Pull in your changes
Using the command line on your remote server, use git pull inside of your wp-content/themes/theme_repo_name directory to pull in your changes to the remote server. Simply type git pull inside the directory and it will make the update. If you have a private repository, it will prompt you for your GitHub username and password in Terminal before pulling in the latest changes.

# You should be up and running now!
These eleven simple steps should help you get your local theme environment synced to your production server using the amazing service that is GitHub.

If you have any questions or want to share your experience, we’d love to hear from you in the comments below. In the meantime, happy building!




# WordPress Project

This is a WordPress starter project for use with Composer. I'll add more documentation when I can, but it's based heavily off of Mark Jaquith's [WordPress Skeleton](https://github.com/markjaquith/WordPress-Skeleton) project. To get started using it, just use the `create-project` composer command:

```
composer create-project johnpbloch/wordpress-project my-site 0.1.4
```

This will create the project in the `my-site` directory. The project uses `public` as the document root, so make sure to take that into account in your host configurations.

This package is meant to kickstart development of your site. It's probably unwise to use it to deploy a site directly to production.

## License

MIT
# wordpress
       

# WordPress Skeleton

This is simply a skeleton repo for a WordPress site. Use it to jump-start your WordPress site repos, or fork it and customize it to your own liking!

## Assumptions

* WordPress as a Git submodule in `/wp/`
* Custom content directory in `/content/` (cleaner, and also because it can't be in `/wp/`)
* `wp-config.php` in the root (because it can't be in `/wp/`)
* All writable directories are symlinked to similarly named locations under `/shared/`.

## Questions & Answers

**Q:** Will you accept pull requests?  
**A:** Maybe — if I think the change is useful. I primarily made this for my own use, and thought people might find it useful. If you want to take it in a different direction and make your own customized skeleton, then just maintain your own fork.

**Q:** Why the `/shared/` symlink stuff for uploads?  
**A:** For local development, create `/shared/` (it is ignored by Git), and have the files live there. For production, have your deploy script (Capistrano is my choice) look for symlinks pointing to `/shared/` and repoint them to some outside-the-repo location (like an NFS shared directory or something). This gives you separation between Git-managed code and uploaded files.

**Q:** What version of WordPress does this track?  
**A:** The latest stable release. Send a pull request if I fall behind.

**Q:** What's the deal with `local-config.php`?  
**A:** It is for local development, which might have different MySQL credentials or do things like enable query saving or debug mode. This file is ignored by Git, so it doesn't accidentally get checked in. If the file does not exist (which it shouldn't, in production), then WordPress will use the DB credentials defined in `wp-config.php`.

**Q:** What is `memcached.php`?  
**A:** This is for people using memcached as an object cache backend. It should be something like: `<?php return array( "server01:11211", "server02:11211" ); ?>`. Programattic generation of this file is recommended.

**Q:** Does this support WordPress in multisite mode?  
**A:** Yes, as of WordPress v3.5 which was released in December, 2012.
