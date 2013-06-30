# execute previous command as root

    sudo !!

Find path for file
==================

    type -a exe

Monitor Log Files
=================

    tail -f /var/log/file

Zip a folder
============

zips `folder/` to `output.zip`

    zip -r output folder

Watch log files
---------------

    tail -f *


Replace all controller in all coffee files with action

    find . -name "*.coffee" | xargs sed -i "" "s/controller/action/g"

Delete all lines starting with console

    find . -name "*.coffee" | xargs sed -i "" "/^ *console/d"

bash scripting
--------------

    #/!bin/bash
    foo=('foo bar' 'foo baz' 'bar baz')
    bar=$(printf ",%s" "${foo[@]}")
    bar=${bar:1}

    echo $bar

extract image from pdf
----------------------
http://stefaanlippens.net/extract-images-from-pdf-documents

    pdfimages -j foo.pdf  bar

convert images
--------------

convert foo.input bar.output

# Nameserver

    dig ns domain

returns the nameserver of the domain

    dig @$ns domain

returns the entries of this domain from $ns
