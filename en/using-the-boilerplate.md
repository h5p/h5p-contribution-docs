## Create a new content type
In order to understand what an H5P content type consists of, please [see our specification documentation](https://h5p.org/documentation/developers/h5p-specification) first.

Afterwards, you can decide to start with a clean slate, or to [use our boilerplate repository](https://github.com/h5p/h5p-boilerplate). It will provide you with an
empty shell of a content type that you can _fill_ with what you need.

### Using the boilerplate repository
Use a shell window and switch to your Drupal development folder.

There run ```git clone https://github.com/h5p/h5p-boilerplate``` to get a copy of the repository onto your system.
To check that it is working, switch to the folder _h5p-boilerplate_. There run ```npm install``` to download
library dependencies that are required to build the content type. Afterwards, run ```npm run build```. This command
should actually create the content type from the source files (in particular it uses [babel.js](https://babeljs.io/) to transpile ES6 to earlier
versions of JavaScript, so it will also run on older browsers). You should be able to find _Hello World_ in the H5P Hub.
It is a very simple content type that doesn't contain much.

As these lines are written, we have one alternative repository branch that you can use. Switch back to the _h5p-boilerplate_ folder
and run ```git checkout question-type``` and build the distribution by running ```npm run build``` (alternatively, you could run
```npm run watch``` which would continuously build the distribution in the background). You will now have a slightly more
elaborated version of the _Hello World_ content type, because the source code already provides you with:
- A language folder containing the default _.en.json_ file that translations to other languages should be based on
- All variables and functions that are required to implement the [Question Type Contract](https://h5p.org/documentation/developers/contracts).
  Having it (with the particular implementation for your purpose) will ensure that your content type can be used in
  compound content types such as Question Set or Column and that reporting will work for a host systems grade book.
- A stub for using the _getCurrentState_ function that is used for storing the state of a content type so users can continue
  where they left off before.
- A second class showing how you could organize your content instead of putting everything into one massive source file.

Now it's your turn! The sky is the limit!
