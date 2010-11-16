$LOAD_PATH.unshift File.expand_path("../lib", __FILE__)
require 'pathname'
require 'tty'

task :build do
  if %x[which brew].strip.empty? then
    onoe "Can't find homebrew installed on your system. Is brew in your path?"
    exit(-1)
  end

  %[brew install #{(Pathname.pwd + 'formulae' + 'mplayer.rb').realpath}]
end

task :stage do
  begin
    require 'extensions/pathname'
    require 'dylibpackager'
  rescue LoadError
    onoe "Can't load mplayerosx-builds libraries, please check your $LOAD_PATH"
    exit(-1)
  end

  lt = DylibPackager.new(Pathname.new(%x[which mplayer].strip))
  lt.stage_to('work')
end