require 'rake'
require 'spec/rake/spectask'

task :default => :spec

Spec::Rake::SpecTask.new(:spec) do |t|
  #t.spec_opts = ['--options', "\"#{File.dirname(__FILE__)}/spec/spec.opts\""]
  t.spec_files = FileList['test/*_spec.rb']
end

desc "Run all specs"
task :spec

desc "Package for CommonJS"
task :commonjs do
  puts "Packaging for CommonJS"
  sh "mkdir lib" unless File.exist? "lib"
  sh "cp mustache.js lib/mustache.js"
  puts "Done."
end

desc "Package for jQuery"
task :jquery do
  puts "Packaging for jQuery"
  source = "mustache-jquery"
  target_jq = "jquery.mustache.js"
  sh "cat #{source}/#{target_jq}.tpl.pre mustache.js #{source}/#{target_jq}.tpl.post > #{target_jq}"
  puts "Done, see ./#{target_jq}"
end

desc "Package for dojo"
task :dojo do
  puts "Packaging for dojo"
  source = "mustache-dojo"
  target_js = "mustache.js"
  sh "mkdir -p dojox; mkdir -p dojox/string"
  sh "cat #{source}/#{target_js}.tpl.pre mustache.js #{source}/#{target_js}.tpl.post > dojox/string/#{target_js}"
  puts "Done, see ./dojox/string/#{target_js} Include using dojo.require('dojox.string.mustache.'); "
end

desc "Package for YUI3"
task :yui3 do
  puts "Packaging for YUI3"
  source = "mustache-yui3"
  target_js = "mustache.js"
  sh "kdir -p yui3; mkdir -p yui3/mustache"
  sh "cat #{source}/#{target_js}.tpl.pre mustache.js #{source}/#{target_js}.tpl.post > yui3/mustache/#{target_js}"
  puts "Done, see ./yui3/mustache/#{target_js}"
end

desc "Remove temporary files."
task :clean do
  sh "git clean -fdx"
end
