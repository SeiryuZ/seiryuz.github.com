# Where our Bootstrap source is installed. Can be overridden by an environment variable.
BOOTSTRAP_SOURCE = ENV['BOOTSTRAP_SOURCE'] || File.expand_path("~/projects/bootstrap")

# Where to find our custom LESS file.
BOOTSTRAP_CUSTOM_LESS = 'bootstrap/less/custom.less'


task :bootstrap => [:bootstrap_js, :bootstrap_css]
task :default => :jekyll

task :jekyll => :bootstrap do
  sh 'jekyll'
end


task :bootstrap_css do |t|
  puts "Copying LESS files"
  Dir.glob(File.join(BOOTSTRAP_SOURCE, 'less', '*.less')).each do |source|
    target = File.join('bootstrap/less', File.basename(source))
    cp source, target if different?(source, target)
  end

  puts "Compiling #{BOOTSTRAP_CUSTOM_LESS}"
  sh 'lessc --compress bootstrap/less/custom.less > bootstrap/css/bootstrap.min.css'
end


task :bootstrap_js do
  require 'uglifier'
  require 'erb'

  paths = []
  minifier = Uglifier.new
  Dir.glob(File.join(BOOTSTRAP_SOURCE, 'js', '*.js')).each do |source|
    base = File.basename(source).sub(/^(.*)\.js$/, '\1.min.js')
    paths << base
    target = File.join('bootstrap/js', base)
    if different?(source, target)
      File.open(target, 'w') do |out|
        out.write minifier.compile(File.read(source))
      end
    end
  end

  sh 'uglifyjs bootstrap/js/* js/main.js -o js/all.js'
end


def different?(path1, path2)
  require 'digest/md5'
  different = false
  if File.exist?(path1) && File.exist?(path2)
    path1_md5 = Digest::MD5.hexdigest(File.read path1)
    path2_md5 = Digest::MD5.hexdigest(File.read path2)
    (path2_md5 != path1_md5)
  else
    true
  end
end
