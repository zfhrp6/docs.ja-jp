### <a name="icommandcanexecutechanged-event-behaviour-changed-in-net-45"></a>ICommand.CanExecuteChanged イベントの動作が .NET 4.5 で変更された

|   |   |
|---|---|
|説明|.NET Framework 4.5 では、イベントの送信元がイベントを発生させたオブジェクトと同じオブジェクトでない限り、<xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=name> は無視されました。 このバグは、.NET Framework 4.5 サービス更新プログラムで修正されました。|
|提案される解決策|このバグは .NET Framework 4.5 サービス リリースで修正されたため、.NET Framework がさ真であることを確認することによって、または .NET Framework 4.5.1 にアップグレードすることによって回避できます。 または、<xref:System.Windows.Input.ICommand?displayProperty=name> を使用しているアプリケーション コードを、<xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=name> コマンドを発生させたときの送信者がイベントを発生させたオブジェクトと同じであるかどうかを確認するように変更できます。|
|スコープ|マイナー|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=nameWithType></li></ul>|
|アナライザー|<ul><li>CD0084</li></ul>|

