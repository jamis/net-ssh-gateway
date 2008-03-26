require './lib/net/ssh/gateway'

begin
  require 'echoe'
rescue LoadError
  abort "You'll need to have `echoe' installed to use Net::SSH::Gateway's Rakefile"
end

version = Net::SSH::Gateway::Version::STRING.dup
if ENV['SNAPSHOT'].to_i == 1
  version << "." << Time.now.utc.strftime("%Y%m%d%H%M%S")
end

Echoe.new('net-ssh-gateway', version) do |p|
  p.changelog        = "CHANGELOG.rdoc"

  p.author           = "Jamis Buck"
  p.email            = "jamis@jamisbuck.org"
  p.summary          = "a pure-Ruby implementation of the SSH2 client protocol"
  p.url              = "http://net-ssh.rubyforge.org/gateway"

  p.need_zip         = true
  p.include_rakefile = true

  p.rdoc_pattern     = /^(lib|README.rdoc|CHANGELOG.rdoc)/
end
