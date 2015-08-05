# Introduction #

Add your content here.

# File Summary #

Looking at your ScratchLIVE directory on your computer (**ScratchLIVE** or similar) you will see something like:

  * dir **Crates**
> > o crate file _Reggae.crate_
> > o crate file _Dancehall\_Reggae.crate_
  * dir **Subcrates**
> > o crate file _Reggae%%New\_Riddim.crate_
> > o crate file _Dancehall\_Reggae%%Club\_Bangers.crate_
  * database file Database V2
  * markup file _neworder.pref_

# Structure of the Database V2 File #

Step one gets the version information, steps two and three get repeated again and again until the end of the file.

The possible fields for each track record are listed here.


  1. First, we need to get the version information. This is the first thing in crate files as well:
    1. **Four bytes** - The key, or name, of the field. Four bytes = four characters in this case. These four characters should make the string vrsn.


> 2. **Four bytes** - A four-byte integer (long, whatever). This integer tells us the number of bytes that make up the value of the field.

> 3. **Num bytes from the prev. int** - This is a two-bytes-per-character string. It should look something like _2.0/Serato Scratch LIVE Database_.

> 2. At this point in the process, if you're getting something outrageous, you should stop what you're doing! The rest of this file is filled out with track records. These track records should be grabbed in the same way as you grabbed the version information:
    1. **Four bytes** - The key, or name, of the field. Four bytes = four characters in this case. These four characters should make the string otrk.

> 2. **Four bytes** - A four-byte integer (long, whatever). This integer tells us the number of bytes that make up the value of the field.

> 3. **Num bytes from the prev. int** - This data should be parsed separately. It has its own set of key->value pairs.

> 3. Parsing the individual track records
    1. **Four bytes** - This again will be the key. These keys will vary (I have a list of them that I will post soon).

> 2. **Four bytes** - A four-byte integer (long, whatever). This integer tells us the number of bytes that make up the value of the field.

> 3. **Num bytes from the prev. int** - This value will vary in type and actual value. Possible types are:
    * Two-byte-per-character string
    * Two-byte single character
    * Four byte integer (long)
    * One byte integer (short)
> 4. Repeat steps 2-3 again and again until you reach the end of the file.