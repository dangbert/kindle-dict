# How to Generate a Kindle Dictionary
Note: Originally inspired by [Michael Sheldon](https://blog.mikeasoft.com/2011/01/05/free-as-in-gpl2-translation-dictionaries-for-the-kindle/). before creating your own dictionary see if he has one on his page already for your language.

Instructions (based on [this article](https://1manfactory.com/create-your-own-kindle-dictionary-for-every-language-for-free/)):

1. Download desired dictionary file from [dict.cc](https://www1.dict.cc/translation_file_request.php)
2. unzip and name txt file something like `dict.cc_EL-EN.txt`
3. Open a termainl, `cd` into the directory containing this source code and run:

````bash
mkdir tmp && cd tmp
../tab2opf.py /path/to/dict.txt -s <SOURCE_LANG> -t <TARGET_LANG>
# for example:
../tab2opf.py ../sources/dict.cc_EL-EN.txt -s el -t en
````

4. Convert outputted .opf file to mobi:

````bash
# download mobigen:
curl http://www.freekindlebooks.org/Dev/Mobi/mobigen/mobigen.exe
# run mobigen (with wine if on linux):
wine64 mobigen.exe ./dict.cc_EL-EN.opf
# file dict.cc_EL-EN.mobi should be created!
````

5. Copy mobi file to Kindle, **and restart the kindle**.
  * Note: if you make a new version of the dictionary later, you may have to give it a different filename as well (even if you delete the original on the kindle first).

---

## More info:

Originally I tried to use the code provided in Michael Sheldon's article but the greek dictionary I created didn't seem to work on the Kindle (I think because the entries were all converted to Latin characters).  I found [this reddit thread](https://www.reddit.com/r/kindle/comments/9rb7hp/how_do_i_create_a_custom_kindle_dictionary/e8fo1uu?utm_source=share&utm_medium=web2x&context=3) and ended up forking [apeyser's repo](https://github.com/apeyser/tab2opf) instead.
