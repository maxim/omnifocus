# -*- ruby -*-

require 'rubygems'
require 'hoe'

Hoe.plugin :seattlerb
Hoe.plugin :isolate

Hoe.spec "omnifocus" do
  developer "aja", "kushali@rubyforge.org"
  developer "Ryan Davis", "ryand-ruby@zenspider.com"

  license "MIT"

  dependency "rb-appscript", "~> 0.6.1"
  dependency "mechanize",    "~> 2.0"

  pluggable!
end

def omnifocus cmd, options = nil
  inc = "-Ilib:../../omnifocus-github/dev/lib:../../omnifocus-redmine/dev/lib"

  ruby "#{options} #{inc} bin/of #{cmd}"
end

task :sync => :isolate do
  omnifocus "sync"
end

task :fix => :isolate do
  omnifocus "fix"
  omnifocus "resch"
end

task :debug => :isolate do
  cmd = ENV["CMD"] || "sync github"
  d = ENV["D"] ? "-d" : nil
  omnifocus cmd, d
end

# vim: syntax=ruby
