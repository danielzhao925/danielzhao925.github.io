---
layout: post
title:  "Swift file manager!"
date:   2016-04-22 15:09:43 +0800
categories: swift update
---

1. Home Directory
var homeDir=NSHomeDirectory()
println("\(dirHome)")

2. Documents Directory
var paths = NSSearchPathForDirectoriesInDomains(NSSearchPathDirectory.DocumentDirectory, NSSearchPathDomainMask.UserDomainMask, true)
    var documentsDirectory = paths[0] as! String
    println("\(documentsDirectory)")

3. Library Directory
    1) var paths = NSSearchPathForDirectoriesInDomains(NSSearchPathDirectory.LibraryDirectory, NSSearchPathDomainMask.UserDomainMask, true)
        var libraryDirectory = paths[0] as! String
        println("\(libraryDirectory)")

    2) var libraryDirectory = NSHomeDirectory().stringByAppendingPathComponent("Library")
      println("\(libraryDirectory)")


4. Cache Directory
var paths = NSSearchPathForDirectoriesInDomains(NSSearchPathDirectory.CachesDirectory, NSSearchPathDomainMask.UserDomainMask, true)
        var cacheDirectory = paths[0] as! String
        println("\(cacheDirectory)")

5. Tmp Directory

    1) var tmpDirectory = NSTemporaryDirectory()
    println("\(tmpDirectory)")

    2) var tmpDirectory = NSHomeDirectory().stringByAppendingPathComponent("tmp")
    println("\(tmpDirectory)");


create folder
var documentDir = NSHomeDirectory().stringByAppendingPathComponent("Documents")
       var fileManager  = NSFileManager.defaultManager()
       var testDir = documentDir.stringByAppendingPathComponent("test")

       var error:NSError?=nil

       var result = fileManager.createDirectoryAtPath(testDir, withIntermediateDirectories: true, attributes: nil, error: &error)

        if result {
            println("success")
        }else {
            println("error:\(error)")
        }

create file
var documentDir = NSHomeDirectory().stringByAppendingPathComponent("Documents")
   var fileManager  = NSFileManager.defaultManager()
   var testDir = documentDir.stringByAppendingPathComponent("test")

   var fileDir = testDir.stringByAppendingPathComponent("test.txt")

   var error:NSError?=nil

   var result = fileManager.createFileAtPath(fileDir, contents: nil, attributes: nil)

    if result {
        println("success")
    }else {
        println("error:\(error)")
    }

write into file
var documentDir = NSHomeDirectory().stringByAppendingPathComponent("Documents")
   var fileManager  = NSFileManager.defaultManager()
   var testDir = documentDir.stringByAppendingPathComponent("test")

   var fileDir = testDir.stringByAppendingPathComponent("test.txt")

   var error:NSError?=nil
   var content = "this is a test"

   var result = content.writeToFile(fileDir, atomically: true, encoding: NSUTF8StringEncoding, error: &error)

    if result {
        println("success")
    }else {
        println("error:\(error)")
    }


read file

var documentDir = NSHomeDirectory().stringByAppendingPathComponent("Documents")
       var fileManager  = NSFileManager.defaultManager()
       var testDir = documentDir.stringByAppendingPathComponent("test")

       var fileDir = testDir.stringByAppendingPathComponent("test.txt")

       var error:NSError?=nil

       var content = NSString(contentsOfFile: fileDir, encoding: NSUTF8StringEncoding, error: &error)

        if error == nil  {
            println("success content:\(content!)")
        }else {
            println("error:\(error)")
        }

check file attributes
var documentDir = NSHomeDirectory().stringByAppendingPathComponent("Documents")
       var fileManager  = NSFileManager.defaultManager()
       var testDir = documentDir.stringByAppendingPathComponent("test")

       var fileDir = testDir.stringByAppendingPathComponent("test.txt")

       var error:NSError?=nil

       var attrs = fileManager.attributesOfFileSystemForPath(fileDir, error: &error)

        if error == nil  {
            println("success content:\(attrs)")
        }else {
            println("error:\(error)")
        }

delete file
var documentDir = NSHomeDirectory().stringByAppendingPathComponent("Documents")
       var fileManager  = NSFileManager.defaultManager()
       var testDir = documentDir.stringByAppendingPathComponent("test")

       var fileDir = testDir.stringByAppendingPathComponent("test.txt")

       var error:NSError?=nil

       var attrs = fileManager.removeItemAtPath(fileDir, error: &error)

        if error == nil  {
            println("success")
        }else {
            println("error:\(error)")
        }

check whether it is a Directory or not

var documentDir = NSHomeDirectory().stringByAppendingPathComponent("Documents")
       var fileManager  = NSFileManager.defaultManager()
       var testDir = documentDir.stringByAppendingPathComponent("test")

       var isDir = ObjCBool(false)
       var existsDir = fileManager.fileExistsAtPath(testDir, isDirectory:&isDir)

        if existsDir {
            println("exists Dir")
        }else {
            println("not exists")
        }
