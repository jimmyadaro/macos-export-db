### What it does

Simple way to export MySQL databases. This was created using  [mac OS' Automator](https://support.apple.com/guide/automator/welcome/mac).

**This is intended to use in macOS XAMPP.**

---

### How it works

1. It asks for the database name

2. It dumps all the databse in your Desktop

---

### DIY

Since this is an Automator app, you can open Automator and do it yourself.

1. Open Automator and select *Application*.

2. Include *Ask for Text* library. Your *Question* can be something like this: *Enter the database name to export* – And mark the *Require an answer* option, so the user cannot bypass the "gimme the database name" part.

3. Include *Run Shell Script* with Bash. Now just include the path to MySQL Dump (this one is for XAMPP) and where you want to save the SQL dump (I'll use the Desktop).

4. (Optional) Add the *Display Notification* library, so you'll be notified when it is done (usually takes ~1 second, it depends on your DB size).

5. Save the App and just use it!

Here is the step 3 code:

```
#$1 is the Ask for Text library response
DB_NAME=$1
#Check your path to MySQL Dump
#Also check where you want to save the SQL Dump
#This will create something like "YOURDB-2018-06-15-1300"
/Applications/XAMPP/xamppfiles/bin/mysqldump -u root $DB_NAME > /Users/$USER/Desktop/$DB_NAME-$(date +%F_%H%M).sql
```

---

### Usage

Open the App, enter the database name and it will just export it!
