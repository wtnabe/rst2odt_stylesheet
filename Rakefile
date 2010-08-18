# -*- mode: ruby -*-

require 'rake/clean'

STYLES      = 'styles'
STYLE_FILES = FileList["#{STYLES}/*", 'sample.rst']
STYLES_OBJ  = "#{STYLES}.odt"
OBJ         = 'sample.odt'
SRC         = 'sample.rst'

CLEAN.include( FileList['**/*~', '**/.DS_Store', '**/*.bak'] )
CLOBBER.include( STYLES_OBJ, OBJ )

desc "compile style files into #{STYLES_OBJ}"
task :compile => STYLES_OBJ do
end

file STYLES_OBJ => STYLE_FILES do
  sh "cd #{STYLES}; zip -r ../#{STYLES_OBJ} *"
end

desc "convert #{SRC} to #{OBJ}"
task :convert => OBJ do
end

file OBJ => STYLES_OBJ do
  sh "rst2odt.py --no-sections --table-border-thickness=17 --stylesheet=#{STYLES_OBJ} #{SRC} #{OBJ}"
end

desc "open converted #{OBJ} file"
task :open => OBJ do
  sh "open #{OBJ}"
end

task :default do
  app = Rake.application
  app.options.show_task_pattern = Regexp.new('')
  app.display_tasks_and_comments
end
