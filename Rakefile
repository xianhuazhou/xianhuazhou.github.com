desc "compile and run the site"
task :default do
  pids = [
    spawn("jekyll serve -w"),
    spawn("scss --watch assets/scss:stylesheets"),
    spawn("jmen -o javascripts/main.js -f assets/coffee/index.js")
  ]

  trap "INT" do
    Process.kill "INT", *pids
    exit 1
  end

  loop do
    sleep 1
  end
end
