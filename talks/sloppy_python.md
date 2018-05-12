# Solve your Problem with Sloppy Python
## Larry Hastings

# Personal Automation

Throw away scripts you're never going to keep

- *Stop writing shell scripts*
- Fail early and noisily
- Have fun!

## Guidelines:

- Use the latest python (f-strings!)
- try automating even more!
- try new libs / technologies
- do what feels good (don't write tests... screw PEP8)

# Deep Dive
## Mass-rename — Old Time Radio

### Aside: hard links

```python
numbers = (1, 2, 3)
# There are two names for the same objects
# File systems on unix have the same concept
```

```bash
ls -l
-rw-r--r-- 1 faris faris 0 DATE # the `1` is the hardlink number
```

## Step 0

You can use backups for yourself using hardlinks

```bash
mkdir backup
for a in * ; do ln $a backup/$a ; done
```

## Step 1: get filenames

Why use `glob`, just do: `ls > x.py`

## Step 2: turn into a big string

## Step 3:  split it up

```python
str.lstrip()
str.rstrip()
str.strip()
str.split([s])

files = """
      thing
      """.strip().split('\n')
```

# Step 4 : disect

```python
for file in files:
  # etc

str.partition(sep) # where sep is '.'
'unce.mp3'.rpartition('.mp3')[0]
# Who needs os.path.splitx()?
```

Tip: test as you go

```python
str.replace(old, new)

for org, new in (
  "Amy", "A mystery"
)

# slow, but fine
```

# step 5: finish

`os.rename()`

# Survey: Provision

laptop, backup laptop, all kinds of ubuntu

`scp server:provision .`

- install 140 packages
- install ssh known keys
- install fonts
- copy personal data
- configure and add `nemo`
- download and build python 2 & 3
- configure tmux, zsh

```python
def install_packages(*args):
  s = " ".join(args)
  if s:
    os.system('sudo apt-get install {}')

  @apt

rsync()

```

`install.my.sincerest.apologies.on.ubuntu.17.10.py`

Example:

`https://github.com/larryhastings/pyweek24`

# Online music vendors

They all have different formats

He wants: `Track (artist) & and m3u file`

`pip install pytaglib`

`decant.bandcamp.py`

# Decant

make a random-named

os.system('unzip' + zipfile)

flatten_dire
read_all_metadata

if we have metadata:

titlecase and clean up artist / album / title

`{artist} - {album}`

`abcde - n` Rip cd

Custom data format as a template


~~`os.system()`~~ -> don't use: doesn't fail early and often

Function you want `subprocess.run(args, check=Tru)`


# BONUS:

```python
def run(s):
  subprocess.run(s, check=True, shell=True)
```
