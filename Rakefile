# -*- mode: ruby -*-

STYLES='styles'

desc "clean up"
task :clean do
  system( "find . -name '*~' -o -name '.DS_Store' | xargs rm" )
end

desc "compile style files into styles.odt"
task :compile => :clean do
  system( "cd #{STYLES}; zip -r ../styles.odt *" )
end

desc "convert reST to .odt"
task :convert => :compile do
  system( 'rst2odt.py --no-sections sample.rst sample.odt' )
end

desc "open converted .odt file"
task :open => :convert do
  system( 'open sample.odt' )
end

task :default do
  app = Rake.application
  app.options.show_task_pattern = Regexp.new('')
  app.display_tasks_and_comments
end
