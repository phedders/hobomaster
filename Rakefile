require 'git'

modules=["hobo", "hobofields", "hobosupport", "hobospec"]

task :default => [:check_modules_file]

file ".gitmodules" do touch ".gitmodules"; end

task :help do
  p "foo"
end

task :check_modules_file => [".gitmodules"] do
  modules.each do |mod|
    system "grep submodule.*#{mod} .gitmodules || git-submodule add git://github.com/tablatom/#{mod}.git #{mod}"
  end
end
  
task :update do
  p "Update"
  system "git-submodule init"
  system "git-submodule update"
  system "git-submodule summary"
end
