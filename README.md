Gitbib
======

Manage references with git. To get started, pick a paper, come up with a
meaningful identifier, attach a legitimate id like a doi, and save in a
yaml file:

```yaml
2015-mdtraj:
  doi: 10.1016/j.bpj.2015.08.015
```

Don't include any metadata that can and should be scraped from a database
somewhere.  You might want to add some tags:

```yaml
2015-mdtraj:
  doi: 10.1016/j.bpj.2015.08.015
  tags: [software, python]
```

And a description:

```yaml
2015-mdtraj:
  doi: 10.1016/j.bpj.2015.08.015
  tags: [software, python]
  description: "MDTraj loads every trajectory format!"
```

You can and should reference other entries from your description:

```yaml
2015-mdtraj:
  doi: 10.1016/j.bpj.2015.08.015
  tags: [software, python]
  description: |+
    MDTraj loads every trajectory format! Cite this paper when you use it.
    
    mdtraj is used by [2016-pyemma] and [2016-msmbuilder3].

2015-pyemma:
  doi: 10.1021/acs.jctc.5b00743
  
2016-msmbuilder3:
  doi: 10.1101/084020
```

Contextualize the work by noting important references from the paper (with
their reference number)

```yaml
2015-mdtraj:
  doi: 10.1016/j.bpj.2015.08.015
  tags: [software, python]
  description: |+
    MDTraj loads every trajectory format! Cite this paper when you use it.
    
    The authors justify their work by noting that
    [2013-lane-milliseconds-folding=2] claims analysis is becoming the
    bottleneck for MD.

2013-milliseconds-folding:
    doi: 10.1016/j.sbi.2012.11.002
```

Details
-------

 - identifier: The key (identifier) must be unique across all input `yaml` files.
   I like all-lowercase, hyphen-spaced identifiers starting
   with the year, optionally middling with the first author's
   last name (if necessary to distinguish), and ending with
   a one-word description of what the paper is about.
 - global identifiers: Right now, we support `doi` and `arxiv`.
 - input files: entries can be loosely organized by choosing
   which input `yaml` file they're entered. Internally,
   everything is concatenated. User-facing organization
   should be exposed through tags. If you want to dump a bunch
   of entries, you should probably put them in a new `yaml` file.
 - The description field uses some markdown-style formatting.
   Paragraph breaks are indicated with blank lines. Otherwise,
   whitespace is trimmed.
   You can include `[links](github.com)` like that.
   
