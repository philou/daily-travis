require 'travis'

desc "Builds the ENV['TRAVIS_REPOSITORY'] travis job with token ENV['GITHUB_TOKEN']"
task :build do
  Travis.github_auth(ENV['GITHUB_TOKEN'])
  Travis::Repository.find(ENV['TRAVIS_REPOSITORY']).last_build.restart
end
