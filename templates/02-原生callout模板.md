<%*
let list = {
  "ℹ️ info" : "info,信息",
  "✏️ note" : "note,笔记",
  "📒 summary" : "summary,summary",
  "🔥 tip" : "tip,提示",
  "☑️ check" : "check,目标",
  "❔ Help" : "help,帮助",
  "⚠️ Warning" : "warning,警告",
  "❌ Fail" : "fail,错误",
  "❔ FAQ": "FAQ,问题",
  "⚡ Danger" : "danger,danger",
  "🪲 Bug" : "bug,bug",
  "📋 Example" : "example,example",
  "✍️ Quote " : "quote,quote",
  "😝 LOL " : "LOL,LOL",
  "📕 Reference " : "REF,Reference"
};
let keys = Object.keys(list);
key = await tp.system.suggester(keys, keys);
let value = list[key];
let index = value.indexOf(",");
let text = value.substring(index+1);
value = value.substring(0, index);
if (key)
    return ">[!" + value + "]+ " + text + "\n> ";
%>