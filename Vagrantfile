require 'json'

config = {}
composer_conf = JSON.parse(File.read("#{__dir__}/composer.json"))
if composer_conf['extra'] && composer_conf['extra']['drupalvm']
  config = composer_conf['extra']['drupalvm']
end

vendor_dir = ENV['COMPOSER_VENDOR_DIR'] || composer_conf.fetch('config', {}).fetch('vendor-dir', 'vendor')

ENV['DRUPALVM_PROJECT_ROOT'] ||= __dir__
ENV['DRUPALVM_CONFIG_DIR'] ||= config.fetch('config_dir', nil)
ENV['DRUPALVM_DIR'] ||= "#{vendor_dir}/geerlingguy/drupal-vm"

# Load the Drupal VM Vagrantfile
load "#{__dir__}/#{ENV['DRUPALVM_DIR']}/Vagrantfile"
