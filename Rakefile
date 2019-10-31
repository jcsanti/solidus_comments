# frozen_string_literal: true

require 'bundler'

Bundler::GemHelper.install_tasks

require 'spree/testing_support/extension_rake'
require 'rspec/core/rake_task'

RSpec::Core::RakeTask.new(:spec)

task default: %i(first_run spec)

task :first_run do
  if Dir['spec/dummy'].empty?
    Rake::Task[:test_app].invoke
    Dir.chdir('../../')
  end
end

desc 'Generates a dummy app for testing'
task :test_app do
  ENV['LIB_NAME'] = 'solidus_comments'
  Rake::Task['extension:test_app'].invoke
end
