require 'rake/clean'
require 'rake/testtask'

lib = File.expand_path('../lib', __FILE__)
$LOAD_PATH.unshift(lib) unless $LOAD_PATH.include?(lib)

require 'cloud/cycler/version'

file "cloudcycler-#{Cloud::Cycler::VERSION}.gem" do
  sh "gem build cloudcycler.gemspec"
end
CLEAN << "cloudcycler-*.gem"

task :build do
  sh "gem build cloudcycler.gemspec"
end

task :rdoc do
  sh 'rdoc lib bin'
end

Rake::TestTask.new do |t|
  t.libs << 'test'
  t.test_files = FileList['test/**/test_*.rb']
end

task :default => "cloudcycler-#{Cloud::Cycler::VERSION}.gem"
task :install => "cloudcycler-#{Cloud::Cycler::VERSION}.gem" do
  sh "gem install ./cloudcycler-#{Cloud::Cycler::VERSION}.gem"
end
