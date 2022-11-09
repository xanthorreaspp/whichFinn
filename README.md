# collectionbuilder-gh-trove

This is a fork of [collectionbuilder-gh](https://github.com/CollectionBuilder/collectionbuilder-gh), customised to generate an exhibition based on a Trove list.

**Demo**: [this exhibition](https://wragge.github.io/trove-wragge-list-demo/) was generated from this [Trove list](https://trove.nla.gov.au/list/83777).

## Instructions for use

This template is intended to be used in conjunction with [this Jupyter notebook](http://glam-workbench.net/trove-lists/#convert-a-trove-list-into-a-collectionbuilder-exhibition) in the GLAM Workbench. The notebook converts [Trove lists](https://trove.nla.gov.au/help/become-voluntrove/lists) into a series of files that can be uploaded to a [CollectionBuilder-GH](https://github.com/CollectionBuilder/collectionbuilder-gh) repository to create an instant exhibition. See the [CollectionBuilder site](https://collectionbuilder.github.io/) for more information on how CollectionBuilder works and what it can do.

#### 1. What you need

* a [Trove API key](https://trove.nla.gov.au/about/create-something/using-api#getting-an-api-key) (copy & paste your key where indicated below)
* a [GitHub account](https://github.com/signup)
* a [Trove List](https://trove.nla.gov.au/help/become-voluntrove/lists) containing items you want to include in your exhibition

#### 2. Setup a GitHub repository for your exhibition

1. Login to your GitHub account.
2. Go to my [customised CollectionBuilder-GH template repository](https://github.com/wragge/collectionbuilder-gh-trove).
3. Click on the big green **Use this template** button.
4. Give your repository a name by typing in the **Repository name** box – the name of the repository will form part of the url for your new exhibition, so you probably want to give it a name that relates to the exhibition.
5. Click on the big green **Create a repository from template** button. You'll be automatically redirected to your new repository.

#### 3. Enable GitHub Pages for your repository

GitHub builds your exhibition from the files in the repository using GitHub Pages. You need to enable this after you create your repository:

1. Click on the **Settings** button in your new repository.
2. Click on the **Pages** button in the side menubar.
3. Under **Branch** select 'main' from the dropdown list and click on **Save**.

GitHub will now build your exhibition. Once it's ready you'll see a link on the 'Pages' page. The url will have the form `https://[your GH user name].github.io/[your repository name]`. At the moment the exhibition will contain dummy data – the next step is to generate your own exhibition data! 

#### 4. Generate your exhibition files from your Trove list

1. Find your Trove list's numeric id. The list id is the number in the url of your Trove list. So [the list](https://trove.nla.gov.au/list/83774) with this url `https://trove.nla.gov.au/list/83774` has an id of `83774`.
2. Copy and paste your *list id* and *Trove API key* where indicated below in this notebook,
3. From the Jupyter **Run** menu select **Run all cells**.
4. When everything has finished running, a link to a zip file will be displayed at the bottom of the notebook. Download it to your own computer and open the zip file. Done!

#### 5. Add more metadata (optional)

The metadata describing the items in your exhibition is contained in the `_data/[list id]-items.csv` file. If the items in your exhibition relate to specific places, you may want to add some extra metadata so that CollectionBuilder can display them on a map.

Information about places is contained in three columns: `location`, `latitude`, and `longitude`. In the `location` field you can include a list of place names, separated by semicolons, eg: 'Melbourne; Sydney; Hobart'. These placenames will be used to build a word cloud when you click on the **Location** tab in your exhibition. 

To add an item to CollectionBuilder's map view, you need to supply values for `latitude` and `longitude`.

You might also want to edit the `subject`, and `description` fields.

1. Open your metadata file with either a text editor or a spreadsheet program (but beware that some programs, like Excel, might mangle your dates).
2. Edit the desired values.
3. Make sure the edited file is saved in CSV (plain text) format, replacing the original metadata file.

Note that GitHub has it's own built-in file editor. So if you don't have a way of editing the CSV file on your own computer, just skip down to the 'Upload your files...' section below and add them to your GitHub repository. To edit the file just view it in GitHub and click on the pencil icon. Once you've finished editing, make sure you click the **Commit** button to save your changes.

#### 6. Replace tiny images (optional)

Trove work records often only include links to tiny thumbnailed versions of images. These don't look great in an exhibition, so you might want to replace them. Different collections use different image viewers, so there's no easy, automated way to do this. You'll have to manually download them and replace the thumnailed versions.

1. From the Trove work record, click on the **View** button and open the link to the original item.
2. Use whatever download mechanism is provided to save a copy of the image on your computer.
3. Rename the downloaded image to match the name of the tiny thumbnailed version in your exhibition's `objects` directory.
4. Replace the thumbnail image in the `objects` directory with the new downloaded version.

#### 7. Upload your files to the exhibition repository

You're now ready to add your exhibition files to the exhibition repository!

1. Go to the GitHub repository you created above.
2. Click on the **Add file** button and select **Upload files**.
3. Select the `_config.yml` file in the exhibition files you downloaded from this notebook.
4. Click on the green **Commit changes** button to save the file in your repository.
5. Open the `_data` directory in your GitHub repository.
6. Click on the **Add file** button and select **Upload files**.
7. Select the `_data/[list id]-items.csv` file in your exhibition files.
8. Click on the green **Commit changes** button to save the file in your repository.
9. Open the `objects` directory in your GitHub repository.
10. Select all the files in the `objects` directory of your exhibition files.
11. Click on the green **Commit changes** button to save the files in your repository.

Once you've uploaded the files, GitHub will rebuild the exhibition using your data. It might take a little while to generate, but once it's ready you see it at `https://[your GH user name].github.io/[your repository name]`.

If your not happy with the metadata and how it displays, you can either edit the exhibition files on your own computer and re-upload them to GitHub. Or you can use GitHub's built-in file editor to make changes. To edit a file just view it in GitHub and click on the pencil icon. Once you've finished editing, make sure you click the **Commit** button to save your changes.

Every time you make a change to your repository, GitHub will automatically rebuild your exhibition.

#### 8. Further customisation

You can further customise the look and feel of your exhibition by editing the `_data/theme.yml` file. For example, you can:

* Set a different `featured-image` to display in the header of your exhibition.
* Change the `latitude` and `longitude` values to set the centre on the map view.

See the [CollectionBuilder documentation](https://collectionbuilder.github.io/cb-docs/docs/theme/) for more options.


#### Annotating Trove list items

You can add your own annotations to Trove list items and these will automatically be included in your exhibition. To add a descriptive note:

1. Make sure you're logged in to your Trove account.
2. Go to your list (you can find a list of your lists in your Trove user profile).
3. Go to the item in your list you want to annotate and click on the **Add list item note button**.
4. Add your note.

Your note will be added to the `description` field of the item when you generate your exhibition files. In addition, any tags added to items in your list will be added to the `subject` field.

Note that if you make changes to your list, you'll need to regenerate the exhibition files using this notebook and upload them to your GitHub repository before the changes are visible in your exhibition.

## License

CollectionBuilder documentation and general web content is licensed [Creative Commons Attribution-ShareAlike 4.0 International](http://creativecommons.org/licenses/by-sa/4.0/). 
This license does *NOT* include any objects or images used in digital collections, which may have individually applied licenses described by a "rights" field.
CollectionBuilder code is licensed [MIT](https://github.com/CollectionBuilder/collectionbuilder-gh/blob/main/LICENSE). 
This license does not include external dependencies included in the `assets/lib` directory, which are covered by their individual licenses.
