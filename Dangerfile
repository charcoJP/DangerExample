
# Make it more obvious that a PR is a work in progress and shouldn't be merged yet
warn("PR is classed as Work in Progress") if github.pr_title.include? "[WIP]"

# Warn when there is a big PR
warn("Big PR") if git.lines_of_code > 500

# github comment settings
github.dismiss_out_of_range_messages

checkstyle_format.base_path = Dir.pwd

# checkstyle
checkstyle_format.report 'app/build/reports/ktlint/ktlint-debug.xml'

# # Android Lint
require 'android_lint_translate_checkstyle_format'
android_lint_xml = ::AndroidLintTranslateCheckstyleFormat::Script.translate(File.read('app/build/reports/lint-results.xml'))
checkstyle_format.report_by_text android_lint_xml
