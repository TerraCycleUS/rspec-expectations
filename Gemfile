source "https://rubygems.org"

gemspec

%w[rspec rspec-core rspec-mocks rspec-support].each do |lib|
  library_path = File.expand_path("../../#{lib}", __FILE__)
  if File.exist?(library_path) && !ENV['USE_GIT_REPOS']
    gem lib, :path => library_path
  else
    gem lib, :git => "git://github.com/rspec/#{lib}.git"
  end
end

### deps for rdoc.info
group :documentation do
  gem 'yard',          '0.8.0', :require => false
  gem 'redcarpet',     '2.1.1', :platform => :mri
  gem 'github-markup', '0.7.2'
end

### dep for ci/coverage
gem 'coveralls', :require => false

# mime-types 2 requires ruby 1.8, so we have to specify an old version.
gem 'mime-types', '~> 1.0'

platforms :jruby do
  gem "jruby-openssl"
end

eval File.read('Gemfile-custom') if File.exist?('Gemfile-custom')
