### <a name="workflow-30-types-are-obsolete"></a>WorkFlow 3.0 タイプは廃止されました

|   |   |
|---|---|
|説明|Windows Workflow Foundation (WWF) 3.0 API (System.Workflow 名前空間からのもの) は廃止されました。|
|提案される解決策|新しい WWF 4.0 API (System.Activities) を代わりに使用する必要があります。 新しい API の使用例は[ここ](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md)にあり、詳しいガイダンスは[ここ](http://blogs.msdn.com/b/workflowteam/archive/2012/02/08/deprecatingwf3.aspx)にあります。 または、WWF 3.0 API はまだサポートされているので、使用でき、ビルド時の警告は、警告を抑制することによって、または以前のコンパイラを使用することによって回避できます。|
|スコープ|Major|
|バージョン|4.5|
|型|再ターゲット中|

