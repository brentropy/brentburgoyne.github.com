desc "Jekyll dev server and sass watch"
task :dev do
  pids = []

  Signal.trap "INT" do
    pids.each { |pid| Process.kill(9, pid)  }
    puts "\n\nGoodby!\n"
  end

  puts "Starting Jekyll development server..."
  pids << Process.spawn("bundle exec jekyll serve -w")

  puts "Watching _scss directory..."
  pids << Process.spawn("bundle exec sass --watch -t compact _scss:css")

  pids.each { |pid| Process.wait(pid) }
end

task :default => [:dev]
