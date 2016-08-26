begin
  require 'jasmine'
  load 'jasmine/tasks/jasmine.rake'
rescue LoadError => e
  p e
  puts e.backtrace.join("\n\t")
  task :jasmine do
    abort 'Jasmine is not available. In order to run jasmine, you must: (sudo) gem install jasmine'
  end
end

require 'rspec/core/rake_task'

task :default => [:spec] # , :'jasmine:ci']

desc 'run ruby tests'
RSpec::Core::RakeTask.new do |task|
  task.pattern = 'spec/**/*_spec.rb'
  task.rspec_opts = ['-f documentation', '--color', '--backtrace']
  task.verbose = false
end

# gem "bundler"
require 'bundler/gem_tasks'

desc 'update deck.js source from ~/dev/deck.js'
task :update_deck do
  Dir.chdir(File.dirname(__FILE__)) do
    sh 'rm -rf public/deck.js/; cp -r ~/dev/deck.js public/; rm -rf public/deck.js/.git'
  end
end

desc 'update deck.js from upstream'
task :upstream_deck do
  sh 'rm -rf public/deck.js'
  sh 'git clone https://github.com/imakewebthings/deck.js.git public/deck.js'
  sh 'rm -rf public/deck.js/.git'
end
