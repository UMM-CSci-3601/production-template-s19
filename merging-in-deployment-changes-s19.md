# Merging in deployment changes

We left a few things out of the `production-template-s19` repository that are necessary for you to be able to deploy your app on a Digital Ocean droplet. This document describes how to merge those changes into your project from the `production-template-s19` repository.

## Add our repository as a remote

You're going to want to merge changes (commits) from our repository into yours, which requires that you add our repository as a _remote_ to your repository. We'll describe how to do this in IntelliJ, but you can definitely do it on the command instead if you prefer.

   * In IntelliJ go to `VCS -> Git -> Remotes…`. 
      * This brings up a little dialog with, currently, one remote, namely the GitHub.com copy of your repository. 
   * Click the `+` button to add a remote
      * Give it whatever name you want (that's just a label so you can find it later). I'm going to use `starter-code` as the name down below.
      * Enter our repo's URL: https://github.com/UMM-CSci-3601/production-template-s19.git
   * Click `OK`

## Decide where/how you're going to merge

The next step is to merge our changes into your repo, but you want to think a little about where/how you want to do that.

The simplest thing is to merge into your `master`, and that's what we'll describe below. If you're going to do that, though, you need to make sure that you've commited or stashed any changes on your current branch so you can switch to `master` and not have things get all muddled.

As an alternative, you could create a new branch from `master` and merge our changes into that. You could then run all the tests, etc., there to confirm that everything is good, and then merge _that_ branch into your `master`. Assuming nothing's changed on your `master` since you created the new branch, that second merge should be trivial and cause no problems. This creates an "unnecessary" second merge, but it means that if something weird happens you can delete that branch and start over without having messed up anything in your `master` branch.

As another alternative, you could check out a clean copy somewhere else, do this merge there, get rid of it after you've pushed up those changes, and then go back to your "working" copy. That's more complicated, but it's easier to step away if something icky happens.

## Merge in our changes

   * Make sure you have the desired target branch checked out (e.g., your `master`).
   * Choose `VCS -> Git -> Merge Changes…`
   * Choose `remotes/starter-code/fix-deployment`
      * Change `starter-code` to whatever name you used for the remote.
      * `fix-deployment` is the name for the branch on _our_ repo that contains all the desired changes. By merging in that branch, you'll get all the commits we made in fixing the deployment problems.
  * Click `Merge`

If you're lucky, that will just work! If you've made a number of changes (especially if you've done a lot of work on `Server.java`) you might end up with merge conflicts that you'll need to resolve. Do that with care, and probably with another pair of eyes to help you double check things.
  
## Run all our tests

Test the heck out things before you push these changes up; you really don't want to have a broken build.

   * The Gradle `runAllTests` task will run both the server and client unit tests, i.e., the JUnit and Karma tests. Do that.
   * Run your E2E tests.

## Push up the changes

Assuming all the tests pass, then push those changes up to GitHub so they're available to everyone in your group.

## Merge those into your working branches

Everyone in your team will want to merge those changes into whatever working branches they have. You _could_ wait and just deal with that when you are wrapping that branch up, but it's probably easier/faster if you do it now as you'll be less likely to have merge conflicts. Again, this is especially true if you are working in `Server.java`.

## You're done!

:smile: :grin: :smile:

Now you can go to the [droplet setup instructions](https://github.com/UMM-CSci-3601/droplet-setup-and-build) and get your droplet up and running!
