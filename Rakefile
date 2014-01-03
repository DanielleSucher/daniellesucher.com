desc "compile and run the site"
task :default do
  pids = [
    spawn("bundle exec jekyll server -w"),
    spawn("scss --watch _assets:stylesheets"),
    spawn("coffee -b -w -o javascripts -c _assets/*.coffee")
  ]
 
  trap "INT" do
    Process.kill "INT", *pids
    exit 1
  end
 
  loop do
    sleep 1
  end
end

task :build do
  `jekyll build`
end

task :deploy => :build do
  `rsync -a --rsh=ssh _site/ danielles@daniellesucher.com:daniellesucher.com/`
end
