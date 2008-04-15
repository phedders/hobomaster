require 'git'

modules=["hobo", "hobofields", "hobosupport", "hobospec", "hobocentral", "agility"]
#modules.push("rdoctest")

task :default => [:check_modules_file,:update]

file ".gitmodules" do touch ".gitmodules"; end

task :help do
  print "HoboMaster repo recorder\n"
  print "See the README for various notes\n\n"
  print "check_modules_file : will check that the .gitmodules file is populated but will not overwrite it - note that this file is updated by the repo anyway\n"
  print "update : runs git-submodule init and update\n"
  print "links :  sets up links to the modules in a local vendor/plugins directory - will search for the vendor plugins directory\n"
  print "update_and_commit / uac :  updates all modules from origin master and commits the master - will record the state of all modules\n"
  print "commit : just commit the state of all modules as they are checked out now - same as git-commit\n"
end

task :check_modules_file => [".gitmodules"] do |task|
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

task :links do
  p "This will setup links to vendor plugin..."
end

task :uac => [:update_and_commit]
task :update_and_commit do |task|
  modules.each do |mod|
    sh "(cd #{mod}; git-pull origin master;)"
  end
  sh "git-commit"
  p "You may want to git-tag this version"
end

# for the confused!
task :commit do sh "git commit"; end
task :summary do sh "git summary"; end
task :log do sh "git log"; end
task :status do sh "git status"; end
