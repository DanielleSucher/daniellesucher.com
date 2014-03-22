desc "compile and run the site"
task :default do
  pids = [
    spawn("bundle exec jekyll server -w"),
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
