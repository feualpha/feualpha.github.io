# frozen_string_literal: true

require 'jekyll'
require 'time'
require 'yaml'

LAYOUT = 'post'
DIR = '_posts/'
DATESTAMP_FORMAT = '%Y-%m-%d'
TIMESTAMP_FORMAT = '%Y-%m-%d %H:%M %z'

namespace :post do
  task :create do
    time = Time.now
    date_stamp = time.strftime DATESTAMP_FORMAT
    time_stamp = time.strftime TIMESTAMP_FORMAT

    print 'title: '
    title = STDIN.gets.chomp

    print 'redirect url: '
    redirect_url = STDIN.gets.chomp

    file_name = Jekyll::Utils.slugify("#{date_stamp}-#{title}") + '.md'
    file_path = DIR + file_name
    content = {
      layout: LAYOUT,
      title: title,
      date: time_stamp,
      redirect_to: [redirect_url]
    }
    File.open(file_path, 'w') do |file|
      file.puts YAML.dump(content) + "---\n"
    end
  end
end
