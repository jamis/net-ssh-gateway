require './lib/net/ssh/gateway'

begin
  require 'echoe'
rescue LoadError
  abort "You'll need to have `echoe' installed to use Net::SSH::Gateway's Rakefile"
end

name = "net-ssh-gateway"
version = Net::SSH::Gateway::Version::STRING.dup
if ENV['SNAPSHOT'].to_i == 1
  version << "." << Time.now.utc.strftime("%Y%m%d%H%M%S")
end

Echoe.new(name, version) do |p|
  p.changelog        = "CHANGELOG.rdoc"

  p.author           = "Jamis Buck"
  p.email            = "net-ssh-gateway@solutious.com"
  p.summary          = "A simple library to assist in establishing tunneled Net::SSH connections"
  p.url              = "http://net-ssh.rubyforge.org/gateway"

  p.dependencies     = ["net-ssh >=1.99.1"]

  p.need_zip         = true
  p.include_rakefile = true

  p.rdoc_pattern     = /^(lib|README.rdoc|CHANGELOG.rdoc)/
end

task 'publish:rdoc' => 'doc/index.html' do
  sh "scp -rp doc/* rubyforge.org:/var/www/gforge-projects/net-ssh/gateway/v1/api/"
end
