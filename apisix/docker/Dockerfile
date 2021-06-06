FROM ubuntu:20.04

# add OpenResty source
wget -qO - https://openresty.org/package/pubkey.gpg | sudo apt-key add -
sudo apt-get update
sudo apt-get -y install software-properties-common
sudo add-apt-repository -y "deb http://openresty.org/package/ubuntu $(lsb_release -sc) main"
sudo apt-get update

# install OpenResty and some compilation tools
sudo apt-get install -y git openresty curl openresty-openssl111-dev make gcc

# install LuaRocks
curl https://raw.githubusercontent.com/apache/apisix/master/utils/linux-install-luarocks.sh -sL | bash -

