task :default => :build
# FIXME: Does this still build gh-pages?

require 'middleman-gh-pages'
require 'pathname'
require 'colorize'

task :slate do
  root     = Pathname.new(__FILE__).parent
  source   = root.join('..', 'slate', 'build').expand_path
  dest     = root.join('docs', 'jsonapi')
  previous = root.join('docs', 'jsonapi.previous')

  cleanup_previous = false
  if source.exist?
    if dest.exist?
      puts "Moving #{dest} to #{previous}"
      FileUtils.mv dest, previous
      cleanup_previous = true
    end
    puts "Copying slate documentation from #{source} to #{dest}"
    FileUtils.cp_r source, dest
    if cleanup_previous
      puts "Cleaning up #{previous}"
      FileUtils.rm_rf previous
    end
  else
    error = <<-ERROR.gsub(/^ {6}/, '')
      Error: Expected to find slate documentation at #{source}

      Please ensure you have:

       - A checkout of Flapjack's slate documentation at #{source.parent}
         (Grab the repo from https://github.com/flapjack/slate)
       - Built a standalone local copy of the slate documentation with a `rake build`.
    ERROR

    puts error.red
  end
end


desc "take site live"
task :deploy do
  system("rsync -auv -e ssh _site/* p:/srv/www/flapjack-project.com/root/")
end

desc "build site"
task :build => [:slate] do
  system('jekyll build')
end