## Translations
By default, H5P uses English, but it will try to present the editor in the language that is set for the host system that H5P is running on,
e.g. WordPress or moodle. Of course, this will fail if there's no translation provided for this particular language. Luckily,
you can contribute them!

If you are interested in some of the technical details, you should visit the [guide for translating libraries](https://h5p.org/documentation/for-developers/translate-h5p-libraries).
Here, we're trying to focus on just the steps you can follow.

### For unexperienced users: Using a text editor
1) Choose a content type that you think needs an update for its translations or translations at all.
2) Go to [https://h5p.org/content-types-and-applications](https://h5p.org/content-types-and-applications) and choose the
   content type, let's say: _True/False Question_
3) On the content type's page (for True/False Question that is [https://h5p.org/true-false](https://h5p.org/true-false))
   look for the link _View source code on Github_. Clicking on it will take you to a new site.
4) Look for the _language_ folder and click on it.
5) a) Find the correct language file for your language, e.g. _fr.json_ for French. Click on it. OR
   b) If there is no language file for your language, click on ".en.json" to get the English version (or any other language
   that you might be able to translate from).
6) On the next page, click on the _raw_ button. Now you're there. You should be able to download the file by
   right-clicking the page. If you downloaded the .en.json file, make sure to rename it to reflect your
   language, e.g. to _jp.json_ for Japanese.
7) Load your file in a text editor of your choice. A simple notepad text editor is enough. You could also use MS Word or some
   other text processing software, but please make sure to save the file as plain text -- but it should not get the suffix
   _.txt_.
8) Just make the changes that you want to suggest. Most words and phrases will appear in the order that they have within
   the editor, so it should not be hard to find what you are looking for. Also, you can always go to the view of the
   content type to check in what context the words and phrases are used. This is often helpful to better grasp the intended
   message of the text.

   You may encounter some peculiar looking things, that may require some extra attention:
   - There may be words prefixed with an @ symbol or a % symbol, e.g. @score or %total. Those are placeholders which will
     be replaced with some other value by the content type. Don't translate these, but keep them as they are.
   - If you want to write a ", you must prefix it with a \. For instance, if one of the labels in the
     editor should be _My "important" label_, the complete line would read:
     _"label": "My \"important\"label"_ (possiibly followed by a _,_).
9) When you're done, just send us the file. We'll take care of the rest.

### For more experiences users: Using github (and git)
If you are familiar with git and/or don't mind having an account on github, the translation process is
pretty much straightforward.

1) Follow steps 1-3 of the guide for unexperienced users or find the right
   repository on github ([https://github.com/h5p/](https://github.com/h5p/)).
2) Fork the repository.
3) a) Clone the repository, e.g. ```git clone https://github.com/yourAccountName/h5p-true-false``` or
   b) Edit the files directly on github.
4) Check the _language_ directory for the file that you need and edit it or
   create a copy of _.en.json_ if there's no language file for your language yet.
   Rename it appropriately, e.g. _su.json_ for Sudanese. Do the required changes
   there. Please note the hints at step 8 of the guide for unexperienced users. Skip the next step if
   you chose to edit the files directly on github.
5) Add `git add *` and commit your changes `git commit -m 'Add changes: What I changed'`.
6) Go to your forked repository on github, log in, click on _Pull request_, check everything,
   and then click on _Create pull request_ to send us the changes.
