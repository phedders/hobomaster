require 'git'

task :default => [:check_modules_file]

file ".gitmodules" 

task :check_modules_file => [".gitmodules"] do
  system "grep submodule.*hobo .gitmodules || git-submodule add git://github.com/tablatom/hobo.git hobo"
  system "grep submodule.*hobofields .gitmodules || git-submodule add git://github.com/tablatom/hobofields.git hobofields"
  system "grep submodule.*hobosupport .gitmodules || git-submodule add git://github.com/tablatom/hobosupport.git hobosupport"
end
  
task :update do
  system "git-submodule init"
  system "git-submodule update"
  
