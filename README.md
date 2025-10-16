# The Build-and-Test manifesto

<a href="https://github.com/JayBazuzi/build-and-test"><img loading="lazy" decoding="async" width="149" height="149" src="https://github.blog/wp-content/uploads/2008/12/forkme_right_darkblue_121621.png" class="attachment-full size-full" alt="Fork me on GitHub"></a>


## Vision

For every source repo in the world, I should be able to clonse it onto a clean machine, run the "build and test" script at the root, and it should just work.

## Values

 | We Value These                                               |
 |--------------------------------------------------------------|
 | Reliable                                                     |
 | Readable and Succinct                                        |
 | Works on a clean machine - do not assume prerequisites       |
 | Mimics CI build definition                                   |

 | Over These                                                   |
 |--------------------------------------------------------------|
 | Fast                                                         |
 | Flexible - "build but don't run tests" or "build for 32-bit" |

That is, while there is value in the items in the lower table, we value the items in the upper more.

## Measures
A newbie can clone your repo, run build-and-test, and see a successful result.

People who understand the script are willing to run it - it doesn't turn them off due to being confusing or leaving a mess on the machine.

## Obstacles
What if you implement this on Mac and I work on Windows? How do we make it work well for both?

What if you implement this on Mac OSX 10.14 and a year later someone wants to run on Mac OSX 10.15? How do we make it work well as the OS changes?

Is it really OK to install, say, a specific version of Visual Studio in this script? I think no. What are the right boundaries for what this script should and shouldn't do?

## Methods
Place a script in the root of the repo named `build-and-test`.

Write it in a language that your target audience will already have. CMD + Bash are good candidates. Since it's simple, it's OK to dual-implement in two native script languages.

Call out to other tools to do the heavy lifting. This script doesn't implement your build, it invokes your build. I human can then read this script to learn how to invoke your build, and then manually mimic it with variation for other needs.

## Collaborators
Consider a script that will configure a clean machine to be a usable development environment for this project. See [https://github.com/JayBazuzi/machine-setup](https://github.com/JayBazuzi/machine-setup).

