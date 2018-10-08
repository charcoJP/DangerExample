
# Make it more obvious that a PR is a work in progress and shouldn't be merged yet
warn("PR is classed as Work in Progress") if github.pr_title.include? "[WIP]"

# Warn when there is a big PR
warn("Big PR") if git.lines_of_code > 500

# github comment settings
github.dismiss_out_of_range_messages

checkstyle_format.base_path = Dir.pwd

# checkstyle
checkstyle_format.report 'app/build/reports/checkstyle/checkstyle.xml'

# ktlint
checkstyle_format.report 'app/build/reports/ktlint/ktlint-debug.xml'

# Android Lint
android_lint.gradle_task = "app:lint"
android_lint.report_file = "app/build/reports/lint-results.xml"
android_lint.filtering = true # 新規追加, 変更のみを対象とする
android_lint.lint

# Findbugs
require 'findbugs_translate_checkstyle_format'
findbugs_xml = ::FindbugsTranslateCheckstyleFormat::Script.translate(File.read('app/build/reports/findbugs/findbugs.xml'))
checkstyle_format.report_by_text findbugs_xml