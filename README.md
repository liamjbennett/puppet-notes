#Puppet Notes and Patterns

A set of notes on patterns, bugs and other useful information.

##Design Patterns


Comma at the end of a resource - breaks ruby 1.8.7
params vs config hash

validate osfamily
validate ports, urls

anchor or not to anchor
require vs ->

defined vs ensure_resource vs con…
   - http://grokbase.com/t/gg/puppet-users/143zdrfwte/is-ensure-resource-evil
 don’t reference variables from other modules

cross-module dependencies + wrapper classes

Always provide an ensure to clean up after yourself

exec
  - when to type/provider
  - onlyif and unless


Symlink pattern

Multiple instance support

how to manage multiple clusters in the same environment?


http://grokbase.com/t/gg/puppet-users/143zdrfwte/is-ensure-resource-evil
Ensure_resource() is evil. Create_resources() is not. The post from
which you excerpted my comment (
https://groups.google.com/forum/#!searchin/puppet-users/ensure_resource/puppet-users/dOCIZ8-Gfgw/VhlBbrSRpb8J)


##Bugs and edge cases


multi-line rspec-puppet tests - breaks ruby 1.8.7

pin puppetlabs_spec_helper to 0.4.1

pin rspec to 2.99.0

Square brackets in titles

Silent failing hiera (missing :: )

hiera_hash containing arrays breaks deep_merge

escaping in hiera pre 1.4 https://tickets.puppetlabs.com/browse/HI-127

    %%{}{type}

##Other useful info

    if ENV['PUPPET_DEBUG']
      Puppet::Util::Log.level = :debug
      Puppet::Util::Log.newdestination(:console)
    end

Dumping the catalog in rspec:

    it { p subject.resources }
    it { p subject.resource('User', 'foo') }

Testing templates:

    cat #{file} | erb -x -T - | ruby -c
