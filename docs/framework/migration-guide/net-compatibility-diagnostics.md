---
title: ".NET 互換性診断 |Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e481270-b62a-4cb4-8dda-5b4c5b59d61d
caps.latest.revision: 7
author: twsouthwick
ms.author: tasou
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 19006cc5f24ffc66b92e53e8174c6bd33c249679
ms.openlocfilehash: 06ebf87e02c8fd745d9c2f3a55eca329323a7d91
ms.lasthandoff: 04/18/2017

---
# <a name="net-compatibility-diagnostics"></a>.NET 互換性診断
.NET 互換性診断は、.NET Framework のバージョン間のアプリケーション互換性問題の識別に役立つ Roslyn を使用したアナライザーです。 この一覧には、使用可能なすべてのアナライザーが含まれますが、特定の移行に適用されるのは、その一部分のみです。 アナライザーは、計画的な移行に該当する問題と表面上の問題にすぎないものを判断します。 影響を受けるバージョンによって分割される問題については、[アプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility.md)を参照してください。  
  
 各問題には、次の情報が含まれます。  
  
-   以前のバージョンからの変更点の説明。  
  
-   提案される解決策は、変更が顧客に与える影響と、バージョン間で互換性を保つための回避策があるかどうかの説明です。  
  
-   変更の重要性の評価。 アプリケーション互換性問題は、次のように分類されます。  
  
    |||  
    |-|-|  
    |Major|多数のアプリに影響するか、コードの大幅な変更を必要とする重大な変更。|  
    |マイナー|少数のアプリに影響するか、コードにわずかな変更を加える必要がある変更。|  
    |エッジ ケース|非常に限られた一般的でないシナリオでアプリに影響を与える変更。|  
    |透明|アプリケーションの開発者やユーザーには大きな影響を及ぼさない変更。|  
  
-   バージョンは、フレームワークで変更が最初に適用されたバージョンを示します。 一部の変更は元に戻されることがあり、それも示されます。  
  
-   変更の種類：  
  
    |||  
    |-|-|  
    |再ターゲット中|変更は、新しいバージョンの .NET Framework 向けに再コンパイルされるアプリに影響します。|  
    |ランタイム|変更は、以前のバージョンの .NET Framework 向けだが、その後のバージョンでも実行する既存のアプリに影響します。|  
  
-   影響を受ける API (ある場合)。  
  
-   使用可能な診断の ID  
  
<a name="diagnostic1"></a>   
## <a name="1-soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a>1: SoapFormatter は、ハッシュテーブルなどの順序付けられたコレクション オブジェクトを逆シリアル化できません  
  
|||  
|-|-|  
|詳細|SoapFormatter は、特定のバージョンの .NET Framework でシリアル化されたオブジェクトが別のバージョンで正常に逆シリアル化されることを保証しません。 具体的には、(ハッシュテーブルのような) 順序付けられたコレクションの中には、4.0 と 4.5 の間でメンバーが追加されたものがあり、このような種類のオブジェクトが .NET 4.5 でシリアル化された場合、.NET 4.0 では逆シリアル化できません。 シリアル化データのシリアル化と逆シリアル化の両方が同じバージョンの .NET Framework で行われた場合、問題は発生しないことに注意してください。|  
|提案される解決策|SoapFormatter のシリアル化は、.NET Framework の変更に対応できる BinaryFormatter のシリアル化または NetDataContractSerialization に置き換える必要があります。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize%28System.IO.Stream%29?displayProperty=fullName><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize%28System.IO.Stream%2CSystem.Runtime.Remoting.Messaging.HeaderHandler%29?displayProperty=fullName><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize%28System.IO.Stream%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize%28System.IO.Stream%2CSystem.Object%2CSystem.Runtime.Remoting.Messaging.Header%5B%5D%29?displayProperty=fullName>|  
|アナライザー|CD0001B<br /><br /> CD0001A|  
  
<a name="diagnostic3"></a>   
## <a name="3-wpf-datatemplate-elements-are-now-visible-to-uia"></a>3: WPF DataTemplate 要素が UIA に表示されるようになりました  
  
|||  
|-|-|  
|詳細|以前は、DataTemplate 要素は、UI オートメーションには表示されませんでした。 4.5 から、UI オートメーションは、これらの要素を検出します。 これは、多くの場合に便利ですが、DataTemplate 要素を含まない UIA ツリーに依存するテストは中断することがあります。|  
|提案される解決策|このアプリの UI オートメーション テストを更新して、以前は非表示の DataTemplate 要素を含んでいる UIA ツリーに対応できるようにしなければならないことがあります。 たとえば、いくつかの要素が互いに隣り合っていることを予期しているテストでは、以前は非表示であった UIA 要素が間にあることを予期する必要があります。 または、UIA 要素の特定のカウントまたはインデックスに依存するテストは、新しい値で更新しなければならないことがあります。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Windows.DataTemplate.%23ctor?displayProperty=fullName><br /><br /> <xref:System.Windows.DataTemplate.%23ctor%28System.Object%29?displayProperty=fullName>|  
|アナライザー|CD0003|  
  
<a name="diagnostic4"></a>   
## <a name="4-wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>4: WPF TextBox で選択されているテキストは、テキスト ボックスがアクティブでないとき、異なる色で表示されます  
  
|||  
|-|-|  
|詳細|.NET 4.5 では、WPF テキスト ボックス コントロールがアクティブでないとき (フォーカスがないとき)、ボックス内で選択されているテキストは、コントロールがアクティブなときとは別の色で表示されます。|  
|提案される解決策|[FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported](https://msdn.microsoft.com/library/system.windows.frameworkcompatibilitypreferences.areinactiveselectionhighlightbrushkeyssupported\(v=vs.110\).aspx)プロパティを false に設定することによって、以前の (.NET 4.0 の) 動作を復元できます。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Windows.Controls.TextBox?displayProperty=fullName>|  
|アナライザー|CD0004|  
  
<a name="diagnostic5"></a>   
## <a name="5-listtforeach-can-throw-exception-when-modifying-list-item"></a>5: List\<T>.ForEach は、リスト項目を変更すると、例外をスローすることがあります。  
  
|||  
|-|-|  
|詳細|.NET 4.5 から、`List<T>.ForEach`列挙子は、呼び出し元のコレクション内の要素が変更された場合、InvalidOperationException 例外をスローします。 以前は、この様な場合、例外はスローされませんでしたが、競合状態になることがありました。|  
|提案される解決策|理想的には、安全な操作ではないため、要素の列挙中にリストを変更しないようにコードを修正する必要があります。 ただし、以前の動作に戻すには、アプリを .NET 4.0 向けにできます。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|再ターゲット中|  
|影響を受ける API|<xref:System.Collections.Generic.List%601.ForEach%28System.Action%7B%600%7D%29?displayProperty=fullName>|  
|アナライザー|CD0005|  
  
<a name="diagnostic6"></a>   
## <a name="6-systemuri-parsing-adheres-to-rfc-3987"></a>6: System.Uri 解析は RFC 3987 に準拠します。  
  
|||  
|-|-|  
|詳細|.NET 4.5 では、URI 解析がいくつかの点で変更されました。 ただし、これらの変更は .NET 4.5 を対象としたコードのみに影響することに注意してください。 バイナリが .NET 4.0 を対象としている場合、以前の動作が実行されます。 .NET 4.5 での URI 解析の変更は次のとおりです。<br /><br /> URI 解析は、RFC 3987 の最新の IRI 規則に従って、正規化と文字チェックを実行します。<br /><br /> Unicode 正規化フォーム C は、URI のホスト部分でのみ実行されます。<br /><br /> 無効な mailto: URI は、例外の原因になります。<br /><br /> パス セグメントの最後の末尾のドットが保存されるようになりました。<br /><br /> `file://`URI は、`?`文字をエスケープしません。<br /><br /> Unicode 制御文字の`U+0080`から`U+009F`まではサポートされません。<br /><br /> コンマ文字`,`または`%2c`は自動的にエスケープ解除されません。|  
|提案される解決策|古い .NET 4.0 URI 解析セマンティクスが必要な場合 (めったにありません)、.NET 4.0 を対象とすることによって使用できます。 これは、アセンブリで TargetFrameworkAttribute を使用することによって、または、[プロジェクトのプロパティ] ページの Visual Studio のプロジェクト システム UI によって実現できます。|  
|スコープ|Major|  
|バージョン|4.5|  
|型|再ターゲット中|  
|影響を受ける API|<xref:System.Uri.%23ctor%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29?displayProperty=fullName><br /><br /> <xref:System.Uri.%23ctor%28System.Uri%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.TryCreate%28System.String%2CSystem.UriKind%2CSystem.Uri%40%29?displayProperty=fullName><br /><br /> <xref:System.Uri.TryCreate%28System.Uri%2CSystem.String%2CSystem.Uri%40%29?displayProperty=fullName><br /><br /> <xref:System.Uri.TryCreate%28System.Uri%2CSystem.Uri%2CSystem.Uri%40%29?displayProperty=fullName>|  
|アナライザー|CD0006D<br /><br /> CD0006C<br /><br /> CD0006F<br /><br /> CD0006E<br /><br /> CD0006A<br /><br /> CD0006G<br /><br /> CD0006B|  
  
<a name="diagnostic10"></a>   
## <a name="10-systemuri-escaping-now-supports-rfc-3986-httptoolsietforghtmlrfc3986"></a>10: System.Uri エスケープは RFC 3986 (http://tools.ietf.org/html/rfc3986) をサポートするようになりました。  
  
|||  
|-|-|  
|詳細|URI エスケープは、.NET 4.5 で、[RFC 3986](http://tools.ietf.org/html/rfc3986)をサポートするように変更されました。 具体的な変更内容:<br /><br /> `EscapeDataString` は、予約されている文字を RFC 3986 に基づいてエスケープします。<br /><br /> `EscapeUriString` は、予約されている文字をエスケープしません。<br /><br /> `UnescapeDataString` は、無効なエスケープ シーケンスが発生した場合に例外をスローしません。<br /><br /> 予約されていないエスケープ文字はエスケープ解除されます。|  
|提案される解決策|無効なエスケープ シーケンスの場合、UnescapeDataString のスローに依存しないように、アプリケーションを更新します。 このようなシーケンスは、直接削除する必要があります。<br /><br /> 同様に、エスケープおよびエスケープ解除された URI とデータ文字列は、.NET 4.0 と .NET 4.5 で異なる場合があるため、.NET のバージョン間で直接比較しないでください。 代わりに、1 つの .NET バージョンで解析と正規化を行ってから比較してください。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Uri.EscapeDataString%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.EscapeUriString%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.UnescapeDataString%28System.String%29?displayProperty=fullName>|  
|アナライザー|CD0010A<br /><br /> CD0010B<br /><br /> CD0010C|  
  
<a name="diagnostic11"></a>   
## <a name="11-systemnetpeertopeercollaboration-unavailable-on-windows-8"></a>11: System.Net.PeerToPeer.Collaboration は、Windows 8 では使用できません。  
  
|||  
|-|-|  
|詳細|System.Net.PeerToPeer.Collaboration 名前空間は、Windows 8 以上では使用できません。|  
|提案される解決策|Windows 8 以上をサポートするアプリは、この名前空間またはそのメンバーに依存しないように更新する必要があります。|  
|スコープ|Major|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Net.PeerToPeer.Collaboration?displayProperty=fullName>|  
|アナライザー|CD0011|  
  
<a name="diagnostic12"></a>   
## <a name="12-mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>12: MEF カタログはIEnumerable を実装するため、シリアライザーの作成には使用できなくなりました。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.5 から、MEF カタログは IEnumerable を実装するため、シリアライザー (XmlSerializer オブジェクト) の作成には使用できなくなりました。 MEF カタログをシリアル化しようとすると、例外がスローされます。|  
|提案される解決策|シリアライザーの作成に MEF を使用できなくなりました。|  
|スコープ|Major|  
|バージョン|4.5|  
|型|ランタイム|  
|アナライザー|CD0012|  
  
<a name="diagnostic13"></a>   
## <a name="13-missing-target-framework-moniker-results-in-40-behavior"></a>13: ターゲット フレームワーク モニカーがないと、4.0 の動作になります。  
  
|||  
|-|-|  
|詳細|アセンブリ レベルで [TargetFrameworkAttribute](https://msdn.microsoft.com/library/system.runtime.versioning.targetframeworkattribute\(v=vs.110\).aspx) が適用されていないアプリケーションは、自動的に .NET Framework 4.0 のセマンティクス (quirks) を使用して実行します。 高い品質を確保するには、すべてのバイナリを、ビルドされた .NET Framework のバージョンを示す TargetFrameworkAttribute で明示的に属性指定することをお勧めします。 プロジェクト ファイルでターゲット フレームワーク モニカーを使用すると、MSBuid は TargetFrameworkAttribute を自動的に適用します。|  
|提案される解決策|[ターゲット フレームワーク属性](https://msdn.microsoft.com/library/system.runtime.versioning.targetframeworkattribute\(v=vs.110\).aspx)は、属性をアセンブリに直接追加するか、[プロジェクト ファイルで、または Visual Studio のプロジェクト プロパティ GUI](http://blogs.msdn.com/b/visualstudio/archive/2010/05/19/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework.aspx) でターゲット フレームワークを指定することによって指定する必要があります。|  
|スコープ|Major|  
|バージョン|4.5|  
|型|ランタイム|  
|アナライザー|CD0013|  
  
<a name="diagnostic14"></a>   
## <a name="14-no-longer-able-to-set-enableviewstatemac-to-false"></a>14: EnableViewStateMac を false に設定できなくなりました。  
  
|||  
|-|-|  
|詳細|ASP.NET では、開発者は `<pages enableViewStateMac="false"/>` または `<@Page EnableViewStateMac="false" %>` を指定できなくなりました。 ビュー ステートのメッセージ認証コード (MAC) は、ビュー ステートが埋め込まれたすべての要求に強制されています。 EnableViewStateMac プロパティを明示的に false に設定するアプリだけが影響を受けます。|  
|提案される解決策|EnableViewStateMac は true であると想定する必要があり、結果としての MAC エラーを解決する必要があります ([この](https://support.microsoft.com/kb/2915218)ガイダンスで説明されているように、MAC エラーの原因の詳細によって複数の解決策があります)。|  
|スコープ|Major|  
|バージョン|4.5.2|  
|型|ランタイム|  
|アナライザー|CD0014|  
  
<a name="diagnostic18"></a>   
## <a name="18-blockingcollectionttrytakefromany-does-not-throw-anymore"></a>18: BlockingCollection\<T>TryTakeFromAny はスローしなくなりました。  
  
|||  
|-|-|  
|詳細|入力コレクションの 1 つに完了のマークが付けられた場合、`BlockingCollection<T>.TryTakeFromAny(BlockingCollection<T>[], T)` -1 を返さず、`BlockingCollection<T>.TakeFromAny`例外をスローしなくなりました。 この変更の結果、コレクションの 1 つが空であったり完了していても、他のコレクションに取得できる項目がある場合にコレクションで作業をすることができるようになりました。|  
|提案される解決策|-1 を返す TryTakeFromAny またはスローする TakeFromAny が制御フロー目的で使用されていた場合、ブロッキング コレクションが完了する場合、そのようなコードは、その条件を検出するように `.Any(b => b.IsCompleted)` を使用するように変更される必要があります。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%29?displayProperty=fullName><br /><br /> <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%29?displayProperty=fullName><br /><br /> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%2CSystem.Int32%29?displayProperty=fullName><br /><br /> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%2CSystem.TimeSpan%29?displayProperty=fullName>|  
|アナライザー|CD0018A<br /><br /> CD0018B|  
  
<a name="diagnostic19"></a>   
## <a name="19-xmlschemaexception-now-sets-line-positions-properly"></a>19: XmlSchemaException は、行位置を正しく設定するようになりました。  
  
|||  
|-|-|  
|詳細|LoadOptions.SetLineInfo 値が Load メソッドに渡され、検証エラーが発生した場合、XmlSchemaException.LineNumber と XmlSchemaException.LinePosition プロパティは行情報を含むようになりました。|  
|提案される解決策|XML の読み込み中に SetLinInfo が使用されるとき、XmlSchemaException.LineNumber と XmlSchemaException.LinePosition は正しく設定されるようになったので、これらのプロパティが設定されないことを想定している例外処理コードは、更新する必要があります。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Xml.Linq.LoadOptions?displayProperty=fullName>|  
|アナライザー|CD0019|  
  
<a name="diagnostic20"></a>   
## <a name="20-systemactivities-is-now-aptca"></a>20: System.Activities は APTCA になりました。  
  
|||  
|-|-|  
|詳細|アセンブリは、AllowPartiallyTrustedCallersAttribute 属性でマークされます。|  
|提案される解決策|派生クラスにSecurityCriticalAttribute のマークを付けることはできません。 以前は、派生クラスには SecurityCriticalAttribute のマークを付ける必要がありました。 ただし、この変更によって生じる実質的な影響はないはずです。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|アナライザー|CD0020|  
  
<a name="diagnostic21"></a>   
## <a name="21-workflow-30-types-are-obsolete"></a>21: WorkFlow 3.0 タイプは廃止されました。  
  
|||  
|-|-|  
|詳細|Windows Workflow Foundation (WWF) 3.0 API (System.Workflow 名前空間からのもの) は廃止されました。|  
|提案される解決策|新しい WWF 4.0 API (System.Activities) を代わりに使用する必要があります。 新しい API の使用例は[ここ](https://msdn.microsoft.com/library/jj205427.aspx)にあり、詳しいガイダンスは[ここ](http://blogs.msdn.com/b/workflowteam/archive/2012/02/08/deprecatingwf3.aspx)にあります。 または、WWF 3.0 API はまだサポートされているので、使用でき、ビルド時の警告は、警告を抑制することによって、または以前のコンパイラを使用することによって回避できます。|  
|スコープ|Major|  
|バージョン|4.5|  
|型|再ターゲット中|  
|アナライザー|CD0021|  
  
<a name="diagnostic22"></a>   
## <a name="22-some-workflow-drag-and-drop-apis-are-obsolete"></a>22: 一部の WorkFlow ドラッグ アンド ドロップ API が廃止されました。  
  
|||  
|-|-|  
|詳細|この WorkFlow ドラッグ アンド ドロップ API は廃止され、アプリが 4.5 向けにリビルドされた場合、コンパイラ警告が発生します。|  
|提案される解決策|複数オブジェクトでの操作をサポートする新しい[DragDropHelper](https://msdn.microsoft.com/library/system.activities.presentation.dragdrophelper\(v=vs.110\).aspx) API を代わりに使用する必要があります。 または、ビルド警告を抑制するか、古いコンパイラを使用して警告を回避できます。 API は、まだサポートされています。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|再ターゲット中|  
|影響を受ける API|<xref:System.Activities.Presentation.DragDropHelper.DoDragMove%28System.Activities.Presentation.WorkflowViewElement%2CSystem.Windows.Point%29?displayProperty=fullName><br /><br /> <xref:System.Activities.Presentation.DragDropHelper.GetCompositeView%28System.Windows.DragEventArgs%29?displayProperty=fullName><br /><br /> <xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem%28System.Windows.DragEventArgs%29?displayProperty=fullName><br /><br /> <xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject%28System.Windows.DependencyObject%2CSystem.Windows.DragEventArgs%2CSystem.Activities.Presentation.EditingContext%29?displayProperty=fullName>|  
|アナライザー|CD0022|  
  
<a name="diagnostic23"></a>   
## <a name="23-new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a>23: 新しい (あいまいな) Dispatcher.Invoke オーバーロードは、異なる動作になる可能性があります。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.5 では、System.Action 型のパラメーターを含む Dispatcher.Invoke に新しいオーバーロードが追加されます。 既存のコードを再コンパイルすると、コンパイラは、Delegate パラメーターを持つ Dispatcher.Invoke メソッドの呼び出しを、System.Action パラメーターを持つ Dispatcher.Invoke メソッドの呼び出しとして解決することができます。 Delegate パラメーターを持つ Dispatcher.Invoke オーバーロードの呼び出しが System.Action パラメーターを持つ Dispatcher.Invoke オーバーロードの呼び出しとして解決された場合、次のような動作の差異が生じることがあります。<br /><br /> 例外が発生した場合、Dispatcher.UnhandledExceptionFilter および Dispatcher.UnhandledException イベントは発生しません。 代わりに、例外は、UnobservedTaskException イベントによって処理されます。<br /><br /> DispatcherOperation など、一部のメンバーの呼び出しは、操作が完了するまでブロックされます。|  
|提案される解決策|あいまいさ (および例外処理またはブロック動作における考えられる相違点) を回避するために、呼び出し元の Dispatcher.Invoke は Invoke 呼び出しの 2 番目のパラメーターとして空の object[] を渡すことで、.NET 4.0 メソッドのオーバーロードに解決されるようにできます。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|再ターゲット中|  
|影響を受ける API|<xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.TimeSpan%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.TimeSpan%2CSystem.Windows.Threading.DispatcherPriority%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.Windows.Threading.DispatcherPriority%2CSystem.Object%5B%5D%29?displayProperty=fullName>|  
|アナライザー|CD0023|  
  
<a name="diagnostic24"></a>   
## <a name="24-encoderparameter-ctor-is-obsolete"></a>24: EncoderParameter ctor は廃止されました。  
  
|||  
|-|-|  
|詳細|`EncoderParameter.EncoderParameter(Encoder, Int32, Int32, Int32)` コンストラクターは廃止され、使用された場合、ビルド警告が発生します。|  
|提案される解決策|`EncoderParameter.EncoderParameter(Encoder, Int32, Int32, Int32)` コンストラクターは引き続き動作しますが、.NET 4.5 のツールでコードを再コンパイルするときに古いビルド警告を回避するには、[EncoderParameter.EncoderParameter (Encoder, Int32, EncoderParameterValueType, IntPtr)](https://msdn.microsoft.com/library/hh875096\(v=vs.110\).aspx) コンストラクターを代わりに使用する必要があります。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|再ターゲット中|  
|影響を受ける API|<xref:System.Drawing.Imaging.EncoderParameter.%23ctor%28System.Drawing.Imaging.Encoder%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>|  
|アナライザー|CD0024|  
  
<a name="diagnostic26"></a>   
## <a name="26-change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a>26: タイムアウト引数を持つ Task.WaitAll メソッドの動作の変更  
  
|||  
|-|-|  
|詳細|.NET 4.5 では、Task.WaitAll の動作が、より一貫性のあるものになりました。<br /><br /> .NET Framework 4 では、これらのメソッドの動作に一貫性がありませんでした。 タイムアウトの期限が切れたとき、メソッド呼び出しの前に 1 つ以上のタスクが完了またはキャンセルされた場合、メソッドは AggregateException 例外をスローしました。 タイムアウトの期限が切れると、メソッド呼び出しの前に完了またはキャンセルされたタスクはなかったが、メソッド呼び出し後に 1 つ以上のタスクがこれらの状態になると、メソッドは false を返しました。<br />.NET Framework 4.5 では、これらのメソッドのオーバーロードは、タイムアウト期限が切れたときにタスクがまだ実行中であった場合は false を返し、入力タスクがキャンセルされ (メソッド呼び出しの前か後かに関わりなく)、他に実行中のタスクがなかった場合に限り、AggregateException 例外をスローします。|  
|提案される解決策|WaitAll 呼び出しが呼び出される前にキャンセルされたタスクを検出する手段として AggregateException がキャッチされていた場合、.NET 4.6 は、すべての待機中タスクがタイムアウトの前に完了した場合に限ってスローするため、そのコードは、代わりに IsCanceled プロパティによって同じ検出を行う必要があります (たとえば、Any(t => t.IsCanceled))。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Threading.Tasks.Task.WaitAll%28System.Threading.Tasks.Task%5B%5D%2CSystem.Int32%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.WaitAll%28System.Threading.Tasks.Task%5B%5D%2CSystem.Int32%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.WaitAll%28System.Threading.Tasks.Task%5B%5D%2CSystem.TimeSpan%29?displayProperty=fullName>|  
|アナライザー|CD0026|  
  
<a name="diagnostic27"></a>   
## <a name="27-change-in-behavior-in-data-definition-language-ddl-apis"></a>27: データ定義言語 (DDL: Data Definition Language) API の動作の変更  
  
|||  
|-|-|  
|詳細|AttachDBFilename が指定されたときの DDL API の動作が、次のように変更されました。<br /><br /> 接続文字列で初期カタログ値を指定する必要がなくなりました。 以前は、AttatchDBFilename と初期カタログの両方が必要でした。<br /><br /> AttatchDBFilename と初期カタログの両方が指定され、指定された MDF ファイルが存在した場合、ObjectContext.DatabaseExists メソッドは true を返します。 以前は、false を返していました。<br /><br /> AttatchDBFilename と初期カタログの両方が指定され、指定された MDF ファイルが存在した場合、ObjectContext.DeleteDatabase メソッドを呼び出すと、ファイルは削除されます。<br /><br /> 接続文字列が存在しない MDF と存在しない初期カタログで AttachDBFilename の値を指定したときに ObjectContext.DeleteDatabase が呼び出された場合、メソッドは InvalidOperationException 例外をスローします。 以前は、SqlException 例外をスローしていました。|  
|提案される解決策|これらの変更により、DDL API を使用するアプリケーションおよびツールの構築が簡単になりました。 これらの変更は、次のシナリオでアプリケーションの互換性に影響を及ぼす可能性があります。<br /><br /> ユーザーは、ObjectContext.DatabaseExists が true を返した場合に ObjectContext.DeleteDatabase を呼び出す代わりに、DROP DATABASE コマンドを直接実行するコードを作成します。 データベースがアタッチされておらず、MDF ファイルが存在する場合、これによって既存のコードが破損します。<br /><br /> ユーザーは、初期カタログと MDF ファイルが存在しないとき、ObjectContext.DeleteDatabase メソッドが InvalidOperationException 例外ではなく、SqlException 例外をスローすることを前提としたコードを作成します。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|ランタイム|  
|アナライザー|CD0027|  
  
<a name="diagnostic28"></a>   
## <a name="28-machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a>28: MachineKey.Encode および MachineKey.Decode メソッドは廃止されました。  
  
|||  
|-|-|  
|詳細|これらのメソッドは今後使用しません。 これらのメソッドを呼び出すコードをコンパイルすると、コンパイラ警告が生成されます。|  
|提案される解決策|推奨される代替手段は、[MachineKey.Protect](https://msdn.microsoft.com/library/system.web.security.machinekey.protect\(v=vs.110\).aspx) と [MachineKey.Unprotect](https://msdn.microsoft.com/library/system.web.security.machinekey.unprotect\(v=vs.110\).aspx) です。 または、ビルド警告を抑制するか、古いコンパイラを使用して警告を回避できます。 API は、まだサポートされています。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|再ターゲット中|  
|影響を受ける API|<xref:System.Web.Security.MachineKey.Decode%28System.String%2CSystem.Web.Security.MachineKeyProtection%29?displayProperty=fullName><br /><br /> <xref:System.Web.Security.MachineKey.Encode%28System.Byte%5B%5D%2CSystem.Web.Security.MachineKeyProtection%29?displayProperty=fullName>|  
|アナライザー|CD0028|  
  
<a name="diagnostic29"></a>   
## <a name="29-the-replace-method-in-odata-urls-is-disabled-by-default"></a>29: OData URL の Replace メソッドは、既定では無効です。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.5 以降では、OData URL の Replace メソッドは既定では無効です。 OData Replace が無効のとき (既定)、replace 関数を含むユーザー要求 (一般的ではない) は失敗します。|  
|提案される解決策|Replace メソッドが必要な場合 (一般的ではない)、[構成設定](https://msdn.microsoft.com/library/system.data.services.configuration.dataservicesfeaturessection.replacefunction.aspx)によって再び有効にできます。 ただし、有効になった replace メソッドはセキュリティの脆弱性を開くことがあり、慎重にレビューしてから使用する必要があります。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Data.Services.DataService%601?displayProperty=fullName>|  
|アナライザー|CD0029|  
  
<a name="diagnostic30"></a>   
## <a name="30-systemservicemodelwebwebservicehost-object-no-longer-adds-a-default-endpoint"></a>30: System.ServiceModel.Web.WebServiceHost オブジェクトは、既定のエンドポイントを追加しなくなりました。  
  
|||  
|-|-|  
|詳細|System.ServiceModel.Web.WebServiceHost オブジェクトは、アプリケーション コードによって明示的なエンドポイントが追加された場合には、既定のエンドポイントを追加しなくなりました。|  
|提案される解決策|ユーザーが既定のエンドポイントに接続できることを期待していて、他の明示的なエンドポイントが WebServiceHost に追加されている場合は、既定のエンドポイントも明示的に追加する必要があります (AddDefaultEndpoints を使用して)。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.ServiceModel.Description.ServiceEndpoint%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%2CSystem.Uri%29?displayProperty=fullName>|  
|アナライザー|CD0030A<br /><br /> CD0030B|  
  
<a name="diagnostic31"></a>   
## <a name="31-eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a>31: EventSource.WriteEvent impls は、受け取ったのと同じパラメーター (と ID) を WriteEvent に渡す必要があります。  
  
|||  
|-|-|  
|詳細|ランタイムは次の内容を指定するコントラクトを強制するようになりました。ETW イベント メソッドを定義する EventSource から派生されたクラスは、イベント ID の後に ETW イベント メソッドが渡されたのと同じ引数を指定して、基底クラス EventSource.WriteEvent メソッドを呼び出す必要があります。|  
|提案される解決策|EventListener がこのコントラクトに違反するイベント ソースのプロセスで EventSource データを読み取った場合、IndexOutOfRangeException 例外がスローされます。|  
|スコープ|マイナー|  
|バージョン|4.5.1|  
|型|ランタイム|  
|アナライザー|CD0031|  
  
<a name="diagnostic32"></a>   
## <a name="32-minfreememorypercentagetoactiveservice-is-now-respected"></a>32： MinFreeMemoryPercentageToActiveService が順守されるようになりました。  
  
|||  
|-|-|  
|詳細|この設定は、WCF サービスをアクティブにするためにサーバー上で使用できなければならない最小メモリを設定します。 OutOfMemoryException 例外を防止することを目的としています。 .NET Framework 4.5 では、この設定には効果はありません。 .NET Framework 4.5.1 では、この設定が守られます。|  
|提案される解決策|Web サーバーで使用できる空きメモリが構成設定によって定義されたパーセンテージよりも小さい場合、例外が発生します。 制約されたメモリ環境で正常に開始し、実行された WCF サービスが今度は失敗することがあります。|  
|スコープ|マイナー|  
|バージョン|4.5.1|  
|型|ランタイム|  
|アナライザー|CD0032|  
  
<a name="diagnostic33"></a>   
## <a name="33-xmltextreader-dtd-entity-expansion-is-limited-to-10000000-characters"></a>33: XmlTextReader DTD エンティティの拡張は、10,000, 000 文字に制限されます。  
  
|||  
|-|-|  
|詳細|DTD エンティティの拡張は 10,000,000 文字までに制限されるようになりました。 DTD エンティティの展開を使用しない XML ファイルの読み込みや、制限された DTD エンティティの展開を使用した XML ファイルの読み込みは、影響を受けません。 DTD エンティティの展開が 10,000,000 文字を超えるファイルは読み込みに失敗し、例外をスローします。|  
|提案される解決策|DTD エンティティの拡張の制限が 10,000, 000 では低すぎる場合には、[XmlReaderSettings.MaxCharactersFromEntities](https://msdn.microsoft.com/library/system.xml.xmlreadersettings.maxcharactersfromentities%28v=vs.110%29.aspx) プロパティで値をオーバーライドできます。 適切な MaxCharactersFromEntity 値を持つ XmlReaderSettings を [XmlReader.Create](https://msdn.microsoft.com/library/System.Xml.XmlReader.Create\(v=vs.110\).aspx) に渡すことができます。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Xml.XmlTextReader.%23ctor?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.Stream%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.Stream%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.Stream%2CSystem.Xml.XmlNodeType%2CSystem.Xml.XmlParserContext%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.TextReader%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.TextReader%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.Stream%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.Stream%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.TextReader%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.TextReader%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.Xml.XmlNodeType%2CSystem.Xml.XmlParserContext%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader?displayProperty=fullName>|  
|アナライザー|CD0033|  
  
<a name="diagnostic35"></a>   
## <a name="35-xslt-style-sheet-exception-message-changed"></a>35: XSLT スタイル シート例外メッセージが変更されました。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.5 では、XSLT ファイルが複雑すぎるときのエラー メッセージのテキストが「スタイル シートが複雑すぎます」です。 以前のバージョンのエラー メッセージは 「XSLT コンパイル エラー」でした。 エラー メッセージのテキストに依存するアプリケーション コードは機能しなくなります。 ただし、例外の種類は同じなので、この変更による実質的な影響はありません。|  
|提案される解決策|このエラー条件からの例外メッセージに依存しているアプリケーション コードを、新しいメッセージを予期するように更新するか、(さらに望ましくは) 変更されていない例外の種類 ([XsltException](https://msdn.microsoft.com/library/system.xml.xsl.xsltexception\(v=vs.110\).aspx)) のみに依存するようにコードを更新します。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Reflection.MethodInfo%2CSystem.Byte%5B%5D%2CSystem.Type%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.String%2CSystem.Xml.Xsl.XsltSettings%2CSystem.Xml.XmlResolver%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XPath.IXPathNavigable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XPath.IXPathNavigable%2CSystem.Xml.Xsl.XsltSettings%2CSystem.Xml.XmlResolver%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XmlReader%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XmlReader%2CSystem.Xml.Xsl.XsltSettings%2CSystem.Xml.XmlResolver%29?displayProperty=fullName>|  
|アナライザー|CD0035|  
  
<a name="diagnostic36"></a>   
## <a name="36-wf-serializes-expressionsliteralt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>36: WF による Expressions.Literal\<T> DateTimes のシリアル化の方法が変わりました (カスタム XAML パーサーは機能しなくなります)。  
  
|||  
|-|-|  
|詳細|関連付けられた [ValueSerializer](https://msdn.microsoft.com/library/system.windows.markup.valueserializer\(v=vs.110\).aspx) オブジェクトは、Second および Millisecond コンポーネントがゼロ以外であり、(DateTime 値については) DateTime.Kind プロパティが Unspecified ではない DateTime または DateTimeOffset オブジェクトを、文字列ではなく、プロパティ要素構文に変換します。 この変更により、DateTime および DateTimeOffset の値をラウンドトリップできます。 入力 XAML が属性構文であると想定するカスタム XAML パーサーは正しく機能しません。|  
|提案される解決策|この変更により、DateTime および DateTimeOffset の値をラウンドトリップできます。 入力 XAML が属性構文であると想定するカスタム XAML パーサーは正しく機能しません。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|アナライザー|CD0036|  
  
<a name="diagnostic37"></a>   
## <a name="37-new-enum-values-in-wpfs-pagerangeselection"></a>37: WPF の PageRangeSelection の新しい列挙値  
  
|||  
|-|-|  
|詳細|2 つの新しいメンバー (CurrentPage および SelectedPage) が [PageRangeSelection](https://msdn.microsoft.com/library/system.windows.controls.pagerangeselection\(v=vs.110\).aspx)列挙型に追加されました。|  
|提案される解決策|ほとんどの場合、これらの変更はユーザー コードに影響しません。 ただし、PageRangeSelection 型に対する Enum.GetNames または Enum.GetValues 呼び出しに特定の数の要素が存在することに依存するコードは、修正する必要があります。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName>|  
|アナライザー|CD0037|  
  
<a name="diagnostic38"></a>   
## <a name="38-wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a>38: WPF DispatcherSynchronizationContext.CreateCopy は、現在のインスタンスの代わりに新しいコピーを返すようになりました。  
  
|||  
|-|-|  
|詳細|.NET Framework 4 では、DispatcherSynchronizationContext.CreateCopy() は、主にパフォーマンスの最適化として、現在のインスタンスへの参照を返しました。 .NET Framework 4.5 では、これが新しいインスタンスになり、参照が等しければ、実行中のスレッドが正しい同期コンテキストにあると結論付けることが初めて可能になりました。  これらの参照の ID をチェックするコードが影響を受ける可能性は低いですが、この変更により、DispatcherSynchronizationContext.CreateCopy を呼び出すコードは、.NET Framework 4.5 以降への移行の一部としてテストする必要があります。|  
|提案される解決策|DispatcherSynchronizationContext.CreateCopy() が新しい SynchronizationContext オブジェクトを返すようになったことに注意してください。  以前は、このように生成された参照の等価性を使用するコードは、実際には、正しいコンテキストにあるかどうかを確認していませんでしたが、.NET 4.5 以降でのビルド時には確認を行います。  問題になる可能性は低いですが、影響を受けるコードのパスをよく調べて、何か問題が生じないかどうか確認する必要があります。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=fullName>|  
|アナライザー|CD0038|  
  
<a name="diagnostic39"></a>   
## <a name="39-systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a>39: System.Threading.Tasks.Task は、オブジェクトが破棄された後、ObjectDisposedException をスローしなくなりました。  
  
|||  
|-|-|  
|詳細|Task.IAsyncResult.AsyncWaitHandle を除き、System.Threading.Tasks.Task メソッドは、オブジェクトが破棄された後、ObjectDisposedException 例外をスローしなくなりました。<br />この変更により、キャッシュされたタスクを使用できるようになりました。 たとえば、メソッドで新しいタスクを割り当てる代わりに、既に完了した操作を表す、キャッシュされたタスクを返すことができます。 これは、タスクの任意のコンシューマーによって破棄されてしまうと、使用不可能になってしまう以前の .NET Framework のバージョンでは不可能でした。|  
|提案される解決策|オブジェクトが破棄されたとき、Task メソッドが ObjectDisposedExceptions をスローしなくなったことに注意してください。 アプリが、タスクが破棄されたことを確認するために、この例外に依存していた場合は、[Task.Status](https://msdn.microsoft.com/library/system.threading.tasks.task.status\(v=vs.110\).aspx) を使用してタスクのステータスを明示的に確認するように、アプリを更新する必要があります。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|ランタイム|  
|アナライザー|CD0039|  
  
<a name="diagnostic40"></a>   
## <a name="40-different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a>40: ObjectContext.CreateDatabase メソッドと DbProviderServices.CreateDatabase メソッドで異なる例外処理  
  
|||  
|-|-|  
|詳細|.NET 4.5 から、データベースの作成が失敗した場合、`CreateDatabase` メソッドは、空のデータベースの削除を試みます。 その操作が成功した場合、元の `SQLException` は伝播されます (.NET 4.0 で常にスローされていた `InvalidOperationException` の代わりに)。|  
|提案される解決策|ObjectContext.CreateDatabase または DbProviderServices.CreateDatabase の実行中に InvalidOperationException をキャッチするときには、SQLExceptions もキャッチする必要があります。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Data.Common.DbProviderServices.CreateDatabase%28System.Data.Common.DbConnection%2CSystem.Nullable%7BSystem.Int32%7D%2CSystem.Data.Metadata.Edm.StoreItemCollection%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName>|  
|アナライザー|CD0040|  
  
<a name="diagnostic41"></a>   
## <a name="41-objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a>41: ObjectContext.Translate と ObjectContext.ExecuteStoreQuery は列挙型をサポートするようになりました。  
  
|||  
|-|-|  
|詳細|.NET 4.0 では、`ObjectContext.Translate` および `ObjectContext.ExecuteStoreQuery` メソッドのジェネリック パラメーター `T` は、列挙型にできませんでした。 このシナリオがサポートされるようになりました。|  
|提案される解決策|.NET 4.0 では、列挙型に対して Translate または ExecuteStoreQuery が呼び出された場合、「0」が返されました。 この動作が望ましい場合は、呼び出しを定数 0 (または同等の列挙型) に置き換えてください。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601%28System.String%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601%28System.String%2CSystem.String%2CSystem.Data.Objects.MergeOption%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.Translate%60%601%28System.Data.Common.DbDataReader%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.Translate%60%601%28System.Data.Common.DbDataReader%2CSystem.String%2CSystem.Data.Objects.MergeOption%29?displayProperty=fullName>|  
|アナライザー|CD0041|  
  
<a name="diagnostic42"></a>   
## <a name="42-enumerableemptytresult-always-returns-cached-instance"></a>42: Enumerable.Empty\<TResult> は、常にキャッシュされたインスタンスを返します。  
  
|||  
|-|-|  
|詳細|.NET 4.5 以降では、`Enumerable.Empty` は、常にキャッシュされた内部インスタンス `IEnumerable<T>` を返します。<br /><br /> 以前は、`Enumerable.Empty` は、API が呼び出された時点で空の `IEnumerable<T>` をキャッシュしました。つまり、`Enumerable.Empty` が迅速かつ同時に呼び出されるような条件では、API の別の呼び出しに対して、型の別のインスタンスが返される可能性がありました。|  
|提案される解決策|以前の動作は非確定的なため、コードがそれに依存している可能性は低いです。 ただし、ありそうにないことですが、空の列挙が比較され、ときには等しくないことが予期されている場合には、`Enumerable.Empty` を使用する代わりに、明示的に空の配列を作成する (`new T[0]`) 必要があります。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Linq.Enumerable.Empty%60%601?displayProperty=fullName>|  
|アナライザー|CD0042|  
  
<a name="diagnostic43"></a>   
## <a name="43-httprequestcontentencoding-property-prohibits-utf7"></a>43: HttpRequest.ContentEncoding プロパティは、UTF7 を禁止します。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.5 以降では、HttpRequests の本文では UTF-7 エンコードは禁止されます。 UTF-7 データの受信を必要とするアプリケーションのデータが、正しくデコードされない場合があります。|  
|提案される解決策|理想的には、HttpRequests で UTF-7 エンコードを使用しないようにアプリケーションを更新する必要があります。 または、[<appSettings>](https://msdn.microsoft.com/library/hh975440\(v=vs.110\).aspx) 要素の `aspnet:AllowUtf7RequestContentEncoding` 属性を使用して、レガシ動作に戻すことができます。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Web.HttpRequest.ContentEncoding?displayProperty=fullName>|  
|アナライザー|CD0043|  
  
<a name="diagnostic44"></a>   
## <a name="44-httputilityjavascriptstringencode-escapes-ampersand"></a>44: HttpUtility.JavaScriptStringEncode は、アンパサンドをエスケープします。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.5 以降、JavaScriptStringEncode はアンパサンド (&) 文字をエスケープします。|  
|提案される解決策|アプリがこのメソッドの以前の動作に依存している場合、構成ファイルの [ASP.NET appSettings 要素](https://msdn.microsoft.com/library/hh975440\(v=vs.110\).aspx) に aspnet:JavaScriptDoNotEncodeAmpersand 設定を追加できます。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Web.HttpUtility.JavaScriptStringEncode%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Web.HttpUtility.JavaScriptStringEncode%28System.String%2CSystem.Boolean%29?displayProperty=fullName>|  
|アナライザー|CD0044A<br /><br /> CD0044B|  
  
<a name="diagnostic46"></a>   
## <a name="46-eventlistener-truncates-strings-with-embedded-nulls"></a>46: EventListener は、null が埋め込まれた文字列を切り詰めます。  
  
|||  
|-|-|  
|詳細|EventListener は、null が埋め込まれた文字列を切り詰めます。 null 文字は、EventSource クラスではサポートされません。 変更は、EventListener を使用してプロセス内の EventSource データを読み取り、null 文字を区切り記号として使用するアプリにのみ影響します。|  
|提案される解決策|可能な場合は、埋め込まれた null 文字を使用しないように EventSource データを更新する必要があります。|  
|スコープ|エッジ|  
|バージョン|4.5.1|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Diagnostics.Tracing.EventListener.%23ctor?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%2CSystem.Diagnostics.Tracing.EventKeywords%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%2CSystem.Diagnostics.Tracing.EventKeywords%2CSystem.Collections.Generic.IDictionary%7BSystem.String%2CSystem.String%7D%29?displayProperty=fullName>|  
|アナライザー|CD0046|  
  
<a name="diagnostic48"></a>   
## <a name="48-obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a>48: ObsoleteAttribute は、WinMD のシナリオで、ObsoleteAttribute と DeprecatedAttribute の両方としてエクスポートします。  
  
|||  
|-|-|  
|詳細|Windows メタデータ ライブラリ (.winmd ファイル) を作成するとき、ObsoleteAttribute 属性は ObsoleteAttribute と Windows.Foundation.DeprecatedAttribute の両方としてエクスポートされます。|  
|提案される解決策|ObsoleteAttribute 属性を使用する既存のソース コードを再コンパイルして、C++/CX または JavaScript からそのコードを実行すると、警告が生成されることがあります。<br /><br /> ObsoleteAttribute と Windows.Foundation.DeprecatedAttribute の両方をマネージ アセンブリのコードに適用することはお勧めしません。ビルド警告が表示されることがあります。|  
|スコープ|エッジ|  
|バージョン|4.5.1|  
|型|再ターゲット中|  
|アナライザー|CD0048A<br /><br /> CD0048B|  
  
<a name="diagnostic49"></a>   
## <a name="49-resolveassemblyreference-task-now-warns-on-dependencies-with-the-wrong-architecture"></a>49: ResolveAssemblyReference タスクは、正しくないアーキテクチャとの依存関係に関する警告を表示するようになりました。  
  
|||  
|-|-|  
|詳細|タスクは警告 MSB3270 を生成します。これは参照または依存関係がアプリのアーキテクチャと一致しないことを示します。 たとえば、これは、anycpu オプションでコンパイルされたアプリに x86 参照が含まれる場合に発生します。 このようなシナリオは、実行時にアプリでエラーが起こった場合に発生することがあります (この場合は、アプリが x64 プロセスとして配置されている場合)。|  
|提案される解決策|影響には 2 つの領域があります。<br /><br /> 再コンパイルすると、アプリが MSBuild の以前のバージョンでコンパイルされたときには現れなかった警告が生成されます。 ただし、警告はランタイム エラーの可能性のある原因を特定するため、調査と対処が必要です。<br /><br /> 警告がエラーとして扱われると、アプリはコンパイルされません。|  
|スコープ|マイナー|  
|バージョン|4.5.1|  
|型|再ターゲット中|  
|アナライザー|CD0049|  
  
<a name="diagnostic51"></a>   
## <a name="51-wpf-textbox-defaults-to-undo-limit-of-100"></a>51: WPF TextBox は、既定では、元に戻す上限が 100 に設定されます。  
  
|||  
|-|-|  
|詳細|.NET 4.5 では、WPF テキスト ボックスの既定の元に戻す上限は 100 です (.NET 4.0 では無制限でした)。|  
|提案される解決策|元に戻す上限が 100 では低すぎる場合、TextBox の UndoLimit プロパティを使用して上限を明示的に設定できます。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Windows.Controls.TextBox?displayProperty=fullName>|  
|アナライザー|CD0051|  
  
<a name="diagnostic55"></a>   
## <a name="55-exceptions-during-unobserved-processing-in-systemthreadingtaskstask-no-longer-propagate-on-finalizer-thread"></a>55: System.Threading.Tasks.Task で監視されていない処理中の例外は、ファイナライザー スレッドに伝播されなくなりました。  
  
|||  
|-|-|  
|詳細|System.Threading.Tasks.Task クラスは非同期操作を表すため、非同期処理中に発生する重大ではないすべての例外をキャッチします。 .NET Framework 4.5 では、例外が監視されていず、コードがタスクを待機していない場合、例外はファイナライザー スレッドに伝播されなくなり、ガベージ コレクション時にプロセスをクラッシュします。 この変更により、Task クラスを使用して、監視されていない非同期処理を実行するアプリケーションの信頼性が向上します。|  
|提案される解決策|アプリが、監視されていない非同期例外のファイナライザー スレッドへの伝播に依存している場合、[TaskScheduler.UnobservedTaskException](https://msdn.microsoft.com/library/system.threading.tasks.taskscheduler.unobservedtaskexception\(v=vs.110\).aspx) イベントの適切なハンドラーを提供することによって、または、[ランタイム構成要素](https://msdn.microsoft.com/library/jj160346%28v=vs.110%29.aspx) を設定することによって、以前の動作を復元できます。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Threading.Tasks.Task.Run%28System.Action%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%28System.Action%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%60%600%7D%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%60%600%7D%7D%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7B%60%600%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7B%60%600%7D%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Start?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Start%28System.Threading.Tasks.TaskScheduler%29?displayProperty=fullName>|  
|アナライザー|CD0055|  
  
<a name="diagnostic58"></a>   
## <a name="58-iasyncresultcompletedsynchronously-property-must-be-correct-for-the-resulting-task-to-complete"></a>58: IAsyncResult.CompletedSynchronously プロパティが正しくなければ、結果のタスクは完了しません。  
  
|||  
|-|-|  
|詳細|TaskFactory.FromAsync を呼び出すとき、IAsyncResult.CompletedSynchronously プロパティの実装が正しくなければ、結果のタスクは完了しません。 つまり、実装が同期的に完了した場合にのみ、このプロパティは true を返す必要があります。 以前は、このプロパティは確認されていませんでした。|  
|提案される解決策|タスクが同期的に完了したときにのみ、IAsyncResult の実装が CompletedSynchronusly プロパティに true を返す場合、中断は発生しません。 ユーザーは、所有する IAsyncResult の実装 (ある場合) を見直して、タスクが同期的に完了したかどうかを正しく評価することを確認する必要があります。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|再ターゲット中|  
|影響を受ける API|<xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.IAsyncResult%2CSystem.Action%7BSystem.IAsyncResult%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.IAsyncResult%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.IAsyncResult%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Threading.Tasks.TaskCreationOptions%2CSystem.Threading.Tasks.TaskScheduler%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Threading.Tasks.TaskCreationOptions%2CSystem.Threading.Tasks.TaskScheduler%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%601%7D%2C%60%600%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%601%7D%2C%60%600%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%602%7D%2C%60%600%2C%60%601%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%602%7D%2C%60%600%2C%60%601%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%604%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%603%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%604%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%603%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName>|  
|アナライザー|CD0058|  
  
<a name="diagnostic59"></a>   
## <a name="59-log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a>59: ObjectContext.CreateDatabase メソッドによって作成されたログ ファイル名は、SQL Server の仕様に一致するように変更されました。  
  
|||  
|-|-|  
|詳細|CreateDatabase メソッドが、直接、または SqlClient プロバイダーと共に Code First と接続文字列の AttachDBFilename 値を使用して呼び出されると、filename.ldf (filename は AttachDBFilename 値によって指定されたファイルの名前) ではなく、filename_log.ldf という名前のログ ファイルを作成します。 この変更により、SQL Server の仕様に従ってログ ファイル名が提供されるため、デバッグ機能が向上します。|  
|提案される解決策|ログ ファイル名がアプリケーションにとって重要な場合、標準の _log.ldf ファイル名形式を予期するように、アプリケーションを更新する必要があります。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName>|  
|アナライザー|CD0059|  
  
<a name="diagnostic60"></a>   
## <a name="60-pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a>60: Page.LoadComplete イベントによって、System.Web.UI.WebControls.EntityDataSource コントロールがデータ バインディングを呼び出さなくなりました。  
  
|||  
|-|-|  
|詳細|`Page.LoadComplete` イベントが原因で、System.Web.UI.WebControls.EntityDataSource コントロールがパラメーターの作成/更新/削除に変更を加えるためにデータ バインディングを呼び出すことがなくなりました。 この変更により、データベースへの不要なアクセスがなくなり、コントロールの値がリセットされるのを防ぐことができるほか、SqlDataSource や ObjectDataSource など、他のデータ コントロールと一貫性の取れた動作になります。 この変更により、アプリケーションが `Page.LoadComplete` イベントのデータ バインディングの呼び出しに依存するような珍しい状況において、異なる動作が生成されるようになりました。|  
|提案される解決策|データバインドの必要がある場合は、ポストバックの前半であるイベントでデータバインドを手動で呼び出します。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|アナライザー|CD0060|  
  
<a name="diagnostic61"></a>   
## <a name="61-webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a>61: WebUtility.HtmlDecode は、無効な入力シーケンスをデコードしなくなりました。  
  
|||  
|-|-|  
|詳細|既定では、デコード メソッドによって無効な入力シーケンスが無効な UTF-16 文字列にデコードされることがなくなりました。 代わりに、元の入力が返されます。|  
|提案される解決策|デコーダーの出力の変更は、UTF-16 データではなくバイナリ データを文字列に格納した場合にのみ影響があります。 この動作を明示的に制御するには、[appSettings](https://msdn.microsoft.com/library/ms228154\(v=vs.110\).aspx) 要素の `aspnet:AllowRelaxedUnicodeDecoding` 属性を true に設定して、レガシ動作を有効にするか、false に設定して、現在の動作を有効にします。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Net.WebUtility.HtmlDecode%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Net.WebUtility.HtmlDecode%28System.String%2CSystem.IO.TextWriter%29?displayProperty=fullName><br /><br /> <xref:System.Net.WebUtility.UrlDecode%28System.String%29?displayProperty=fullName>|  
|アナライザー|CD0061|  
  
<a name="diagnostic63"></a>   
## <a name="63-apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>63: SHA-256 コード署名証明書を使用する ClickOnce で発行されたアプリケーションは、Windows 2003 では失敗することがあります。  
  
|||  
|-|-|  
|詳細|この実行可能ファイルは SHA256 で署名されます。 以前は、コード署名証明書が SHA-1 か SHA-256 に関係なく、SHA 1 で署名されました。 この方法は、次の対象に適用されます。<br /><br /> Visual Studio 2012 以降でビルドされたすべてのアプリケーション。<br /><br /> .NET Framework 4.5 がインストールされているシステム上で、Visual Studio 2010 以前でビルドされたアプリケーション。<br /><br /> さらに、.NET Framework 4.5 以降が存在する場合、コンパイル対象となった .NET Framework のバージョンに関係なく、ClickOnce マニフェストはSHA-256 証明書の SHA 256 で署名されます。|  
|提案される解決策|ClickOnce 実行可能ファイルの署名方法に関するこの変更は、Windows Server 2003 システムにのみ影響を及ぼします。これらのシステムには、KB 938397 をインストールする必要があります。<br /><br /> アプリが .NET Framework 4.0 以前のバージョンをターゲットとしている場合でも、SHA-256 を使用したマニフェストの署名方法の変更により、.NET Framework 4.5 以降のバージョンに対するランタイム依存関係が導入されます。|  
|スコープ|エッジ|  
|バージョン|4.5-4.6|  
|型|再ターゲット中|  
|アナライザー|CD0063|  
  
<a name="diagnostic68"></a>   
## <a name="68-dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a>68: DbParameter.Precision と DbParameter.Scale は、パブリック仮想メンバーになりました。  
  
|||  
|-|-|  
|詳細|DbParameter.Precision と DbParameter.Scale は、パブリック仮想プロパティとして実装されます。 これらは、対応する明示的なインターフェイス実装である DbParameter.IDbDataParameter.Precision と DbParameter.IDbDataParameter.Scale に置き換わります。|  
|提案される解決策|ADO.NET データベース プロバイダーを再構築するとき、これらの違いにより、「override」キーワードが Precision および Scale プロパティに適用される必要があります。 これは、コンポーネントを再構築するときにのみ必要です。既存のバイナリは引き続き機能します。|  
|スコープ|マイナー|  
|バージョン|4.5.1|  
|型|再ターゲット中|  
|影響を受ける API|<xref:System.Data.Common.DbParameter.Precision?displayProperty=fullName><br /><br /> <xref:System.Data.Common.DbParameter.Scale?displayProperty=fullName>|  
|アナライザー|CD0068|  
  
<a name="diagnostic73"></a>   
## <a name="73-dataobjectgetdata-now-retrieves-data-as-utf-8"></a>73: DataObject.GetData は、データを UTF-8 として取得するようになりました。  
  
|||  
|-|-|  
|詳細|.NET Framework 4 を対象とするアプリ、または .NET Framework 4.5.1 以前のバージョンで実行するアプリでは、DataObject.GetData は HTML 形式のデータを ASCII 文字列として取得します。 結果として、非 ASCII 文字 (ASCII コードが 0x7F よりも大きい文字) は 2 つのランダムな文字で表されます。<br /><br /> .NET Framework 4.5 以降を対象とするアプリ、および.NET Framework 4.5.2 で実行するアプリでは、`DataObject.GetData` は HTML 形式のデータを UTF-8 として取得し、これは、0x7F よりも大きい文字を正しく表します。|  
|提案される解決策|HTML 形式の文字列に関するエンコーディング問題に対する回避策を実装し (たとえば、UTF8Encoding.GetString メソッドに渡すことによってクリップボードから取得された HTML 文字列を明示的にエンコードすることによって)、アプリケーションの対象をバージョン 4 から 4.5 に変更する場合、その回避策を削除する必要があります。<br /><br /> 何らかの理由で以前の動作が必要な場合、アプリケーションは .NET Framework 4.0 を対象とすることによって、その動作を取得できます。|  
|スコープ|エッジ|  
|バージョン|4.5.2|  
|型|再ターゲット中|  
|影響を受ける API|<xref:System.Windows.DataObject.GetData%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Windows.DataObject.GetData%28System.String%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Windows.DataObject.GetData%28System.Type%29?displayProperty=fullName>|  
|アナライザー|CD0073|  
  
<a name="diagnostic75"></a>   
## <a name="75-targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>75: 既定のアプリケーション ドメインの TargetFrameworkName は、設定されなかった場合、既定で null に設定されなくなりました。  
  
|||  
|-|-|  
|詳細|TargetFrameworkName は、以前は、明示的に設定されない限り、既定のアプリケーション ドメインでは null でした。 4.6 以降では、既定のアプリケーション ドメインの TargetFrameworkName プロパティは、TargetFrameworkAttribute (ある場合) から派生された既定値を持ちます。 既定以外のアプリケーション ドメインは、明示的にオーバーライドされない限り、既定のアプリケーション ドメイン (4.6 では既定で null に設定されない) から TargetFrameworkName を継承し続けます。|  
|提案される解決策|`AppDomainSetup.TargetFrameworkName` が既定で null に設定されることに依然しないように、コードを更新する必要があります。 このプロパティが引き続き null として評価される必要がある場合、明示的にその値に設定できます。|  
|スコープ|エッジ|  
|バージョン|4.6|  
|型|ランタイム|  
|影響を受ける API|<xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName>|  
|アナライザー|CD0075B<br /><br /> CD0075A|  
  
<a name="diagnostic76"></a>   
## <a name="76-x509certificate2tostringbool-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>76: X509Certificate2.ToString(bool) は、.NET が証明書を処理できないときにスローしなくなりました。  
  
|||  
|-|-|  
|詳細|以前は、このメソッドは、verbose パラメーターとして「true」が渡され、.NET Framework ではサポートされない証明書がインストールされていた場合、スローしました。 現在は、メソッドは成功し、証明書のアクセス不能部分を省いた有効な文字列を返します。|  
|提案される解決策|X509Certificate2.ToString(bool) に依存しているコードは、以前は API がスローしていたような場合には、返される文字列から一部の証明書データ (公開鍵、秘密鍵、拡張子など) が除外されることを予期するように更新する必要があります。|  
|スコープ|エッジ|  
|バージョン|4.6|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString%28System.Boolean%29?displayProperty=fullName>|  
|アナライザー|CD0076|  
  
<a name="diagnostic77"></a>   
## <a name="77-reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>77: リフレクション オブジェクトは、マネージ コードからアウト プロセス DCOM クライアントに渡せなくなりました。  
  
|||  
|-|-|  
|詳細|リフレクション オブジェクトはマネージ コードからアウト プロセス DCOM クライアントに渡されなくなりました。 影響を受ける型は次のとおりです。<br /><br /> Assembly<br /><br /> MemberInfo (および FieldInfo、MethodInfo、Type、TypeInfo を含む派生型)<br /><br /> MethodBody<br /><br /> モジュール<br /><br /> ParameterInfo。<br /><br /> オブジェクトの `IMarshal` の呼び出しは `E_NOINTERFACE` を返します。|  
|提案される解決策|非リフレクション オブジェクトで動作するように、マーシャリング コードを更新します。|  
|スコープ|マイナー|  
|バージョン|4.6|  
|型|ランタイム|  
|アナライザー|CD0077|  
  
<a name="diagnostic78"></a>   
## <a name="78-contentdisposition-datetimes-returns-slightly-different-string"></a>78: ContentDisposition DateTimes は、少し異なる文字列を返します。  
  
|||  
|-|-|  
|詳細|ContentDispositions の文字列表現が更新され、4.6 以降では、常に DateTime の時間コンポーネントを 2 桁で表します。 これは、[RFC822](http://www.ietf.org/rfc/rfc0822.txt) と [RFC2822](http://www.ietf.org/rfc/rfc2822.txt) に準拠しています。 これにより、4.6 では、配置の時間要素の 1 つが午前 10 時より前のシナリオでは、`ContentDisposition.ToString` は少し異なる文字列を返します。 ContentDispositions は、ときには、文字列への変換によってシリアル化されるため、ContentDisposition ToString 操作、シリアル化、または GetHashCode 呼び出しを見直す必要があることに注意してください。|  
|提案される解決策|異なるバージョンの .NET Framework からの ContentDispotisions の文字列表現が互いに正しく対応することを期待しないでください。 可能な場合は、比較を行う前に、文字列を ContentDispositions に戻してください。|  
|スコープ|マイナー|  
|バージョン|4.6|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=fullName><br /><br /> <xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=fullName>|  
|アナライザー|CD0078|  
  
<a name="diagnostic82"></a>   
## <a name="82-workflowdesignerload-doesnt-remove-symbol-property"></a>82: WorkflowDesigner.Load は、シンボル プロパティを削除しません。  
  
|||  
|-|-|  
|詳細|ワークフロー デザイナーで .NET Framework 4.5 を対象とし、再ホストされた 3.5 ワークフローを WorkflowDesigner.Load() メソッドで読み込むと、ワークフローの保存中に XamlDuplicateMemberException がスローされます。|  
|提案される解決策|このバグは、ワークフロー デザイナーで .NET Framework 4.5 を対象とするときにのみ現れるため、`WorkflowDesigner.Context.Services.GetService<DesignerConfigurationService>().TargetFrameworkName` を 4.0 の .NET Framework に設定することによって回避できます。<br /><br /> または、[WorkflowDesigner.Load()](https://msdn.microsoft.com/library/ee403482\(v=vs.110\).aspx) の代わりに、[WorkflowContext.Load(string)](https://msdn.microsoft.com/library/ee425926\(v=vs.110\).aspx) メソッドを使用してワークフローを読み込むことによって、問題を回避できます。|  
|スコープ|Major|  
|バージョン|4.5-4.5.2|  
|型|再ターゲット中|  
|影響を受ける API|<xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=fullName>|  
|アナライザー|CD0082|  
  
<a name="diagnostic83"></a>   
## <a name="83-sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a>83: SqlConnection.Open は、IFS 以外の Winsock BSP または LSP が存在する Windows 7 では失敗します。  
  
|||  
|-|-|  
|詳細|SqlConneciton.Open および OpenAsync は、コンピューター上に IFS 以外の Winsock BSP または LSP が存在する Windows 7 コンピューターで実行している場合、.NET Framework 4.5 では失敗します。<br /><br /> IFS 以外の BSP または LSP がインストールされているかどうかを確認するには、`netsh WinSock Show Catalog` コマンドを使用して、返される `Winsock Catalog Provider Entry` 項目をすべて調べてください。 Service Flags 値の `0x20000` ビットがセットされている場合、プロバイダーは IFS ハンドルを使用していて、正しく機能します。 `0x20000` ビットがクリアされている (セットされていない) 場合は、IFS 以外の BSP または LSP です。|  
|提案される解決策|このバグは .NET framework 4.5.2 で修正されたため、.NET Framework をアップグレードすることによって回避できます。 または、インストールされている IFS 以外の Winsock LSP を削除することによって回避できます。|  
|スコープ|マイナー|  
|バージョン|4.5-4.5.2|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=fullName><br /><br /> <xref:System.Data.SqlClient.SqlConnection.OpenAsync%28System.Threading.CancellationToken%29?displayProperty=fullName>|  
|アナライザー|CD0083|  
  
<a name="diagnostic84"></a>   
## <a name="84-icommandcanexecutechanged-event-behaviour-changed-in-net-45"></a>84: ICommand.CanExecuteChanged イベントの動作が .NET 4.5 で変更されました。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.5 では、イベントの送信元がイベントを発生させたオブジェクトと同じオブジェクトでない限り、CanExecuteChangedEvent は無視されました。 このバグは、.NET Framework 4.5 サービス更新プログラムで修正されました。|  
|提案される解決策|このバグは .NET Framework 4.5 サービス リリースで修正されたため、.NET Framework がさ真であることを確認することによって、または .NET Framework 4.5.1 にアップグレードすることによって回避できます。 または、ICommand を使用しているアプリケーション コードを、CanExecuteChanged コマンドを発生させたときの送信者がイベントを発生させたオブジェクトと同じであるかどうかを確認するように変更できます。|  
|スコープ|マイナー|  
|バージョン|4.5-4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=fullName>|  
|アナライザー|CD0084|  
  
<a name="diagnostic85"></a>   
## <a name="85-some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a>85: 一部の .NET API は、ファースト チャンス (処理済み) EntryPointNotFoundExceptions の原因になります。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.5 で、少数の .NET メソッドは、ファースト チャンス EntryPointNotFoundExceptions をスローするようになりました。 これらの例外は .NET Framework 内で処理されますが、ファースト チャンス例外を予期していないテスト自動化を中断することがありました。 これらと同じ API は、HighVersionLie が有効なとき、一部の ApiVerifier シナリオを中断させます。|  
|提案される解決策|このバグは、.NET Framework 4.5.1 にアップグレードすることによって回避できます。 または、ファースト チャンス EntryPointNotFoundExceptions で中断しないように、テスト自動化を更新できます。|  
|スコープ|エッジ|  
|バージョン|4.5-4.5.1|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Diagnostics.Debug.Assert%28System.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%29?displayProperty=fullName>|  
|アナライザー|CD0085|  
  
<a name="diagnostic86"></a>   
## <a name="86-scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a>86: VirtualizingStackPanel 内の WPF TreeView またはグループ化された ListBox をスクロールすると、ハングすることがあります。  
  
|||  
|-|-|  
|詳細|.NET Framework v4.5 では、仮想化されたスタック パネル内の WPF TreeView をスクロールすると、ビューポートに余白があった場合 (たとえば、TreeView 内の項目間や、ItemsPresenter 要素上)、ハングすることがあります。 さらに、場合によっては、ビュー内にサイズの異なる項目があると、余白がない場合でも、不安定になることがあります。|  
|提案される解決策|このバグは、.NET Framework 4.5.1 にアップグレードすることによって回避できます。 または、含まれているすべての項目が同じサイズである場合は、仮想化されたスタック パネル内のビュー コレクション (TreeView など) から余白を削除できます。|  
|スコープ|Major|  
|バージョン|4.5-4.5.1|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Windows.Controls.VirtualizingPanel.SetIsVirtualizing%28System.Windows.DependencyObject%2CSystem.Boolean%29?displayProperty=fullName>|  
|アナライザー|CD0086<br /><br /> CD0086|  
  
<a name="diagnostic89"></a>   
## <a name="89-typeisassignablefrom-returns-wrong-result-for-generic-variables-with-constraints"></a>89: Type.IsAssignableFrom は、制約を持つジェネリック変数について正しくない結果を返します。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.5 では、Type.IsAssignableFrom は、制約を持ついくつかのジェネリック型について、常に誤って `false` を返します。|  
|提案される解決策|この問題は、サービス更新プログラムで修正されました。 この問題を修正するには、.NET Framework 4.5 を .NET Framework 4.5.1 以降に更新してください。 または、ジェネリック パラメーターに制約があるジェネリック型で IsAssignableFrom を使用しないでください。 リフレクション API を回避策として使用できます。|  
|スコープ|マイナー|  
|バージョン|4.5-4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Type.IsAssignableFrom%28System.Type%29?displayProperty=fullName>|  
|アナライザー|CD0089<br /><br /> CD0089|  
  
<a name="diagnostic91"></a>   
## <a name="91-entityframework-60-loads-very-slowly-in-apps-launched-from-visual-studio"></a>91: EntityFramework 6.0 は、Visual Studio から起動されたアプリを読み込むとき、非常に遅くなります。  
  
|||  
|-|-|  
|詳細|Entity Framework 6.0 を使用するアプリを Visual Studio 2013 から起動すると、非常に遅くなることがあります。|  
|提案される解決策|この問題は、EntityFramework 6.0.2 で修正されます。 パフォーマンス問題を回避するには、EntityFramework を更新してください。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|アナライザー|CD0091|  
  
<a name="diagnostic92"></a>   
## <a name="92-multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a>92: AntiXSSEncoder を使用するとき、複数行の ASP.Net TextBox の間隔が変更されました。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.0 では、`AntiXSSEncoder` を使用する場合、ポストバックの複数行テキスト ボックスの行間に余分な行が挿入されました。 .NET Framework 4.5 では、これらの余分な改行は含まれませんが、web アプリが .NET 4.5 を対象としている場合に限ります。|  
|提案される解決策|4.0 の Web アプリの対象を .NET 4.5 に変更すると、複数行テキスト ボックスが改善され、余分な改行が挿入されなくなります。 これが望ましくない場合は、.NET Framework 4.0 を対象とすることによって、アプリを .NET Framework 4.5 で実行するときにも以前の動作が可能です。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|再ターゲット中|  
|アナライザー|CD0092|  
  
<a name="diagnostic95"></a>   
## <a name="95-concurrentqueuettrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>95: ConcurrentQueue\<T>.TryPeek は、出力パラメーターを介して誤った null を返すことがあります。  
  
|||  
|-|-|  
|詳細|一部のマルチ スレッド シナリオでは、`ConcurentQueue<T>.TryPeek` は true を返すことができますが、出力パラメーターに (正しいピーク値の代わりに) null 値を入れることがあります。|  
|提案される解決策|この問題は、.NET Framework 4.5.1 で修正されます。 この Framework にアップグレードすると、問題が解決されます。|  
|スコープ|Major|  
|バージョン|4.5-4.5.1|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek%28%600%40%29?displayProperty=fullName>|  
|アナライザー|CD0095|  
  
<a name="diagnostic98"></a>   
## <a name="98-multiple-items-in-a-single-tablelayoutpanel-cell-may-be-rearranged"></a>98: 単一の TableLayoutPanel セル内の複数の項目が並べ替えられることがあります。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.5 では、同じ TableLayoutPanel セルに複数の項目がある場合、.NET Framework 4.0 とは別の順序で表示されることがあります。|  
|提案される解決策|この動作は、.NET Framework 4.5 のサービス更新プログラムで元に戻されました。 この問題を修正するには、.NET Framework 4.5 を .NET Framework 4.5.1 以降に更新してください。 または、同じ TableLayourPanel セルに複数の項目を置くというあいまいなケースを避けてください。|  
|スコープ|マイナー|  
|バージョン|4.5-4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Windows.Forms.TableLayoutControlCollection.Add%28System.Windows.Forms.Control%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>|  
|アナライザー|CD0098|  
  
<a name="diagnostic100"></a>   
## <a name="100-foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a>100: foreach 反復子変数は、イテレーション内をスコープとするようになったため、クロージャ キャプチャのセマンティクスが (C#5 では) 異なります。  
  
|||  
|-|-|  
|詳細|C#5 (Visual Studio 2012) 以降では、foreach 反復子変数は、イテレーション内をスコープとします。 このため、変数が foreach のクロージャに含まれないことに依存していたコードは機能しなくなります。 この変更による症状は、デリゲートに渡された反復子変数が、デリゲートが呼び出された時点での値ではなく、デリゲートの作成時点での値として扱われることです。|  
|提案される解決策|理想的には、新しいコンパイラの動作を予期するように、コードを更新する必要があります。 古いセマンティクスが必要な場合は、反復子変数を、ループのスコープ外に明示的に配置される別の変数に置き換えることができます。|  
|スコープ|Major|  
|バージョン|4.5|  
|型|再ターゲット中|  
|アナライザー|CD0100|  
  
<a name="diagnostic101"></a>   
## <a name="101-htmltextwriter-does-not-render-br-element-correctly"></a>101: HtmlTextWriter は、\`<br>\>' 要素を正しく表示しません。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.6 以降では、`HtmlTextWriter.RenderBeginTag()` と `HtmlTextWriter.RenderEndTag()` を `<BR />` 要素を指定して呼び出すと、`<BR />` を 1 つだけ (2 つではなく) 正しく挿入します。|  
|提案される解決策|アプリが余分な `<BR />` タグに依存している場合は、`HtmlTextWriter.RenderBeginTag()` をもう一度呼び出す必要があります。 この動作の変更は、.NET Framework 4.6 を対象とするアプリにのみ影響するので、以前の動作を得るためには、以前のバージョンの .NET Framework を対象とするという方法もあります。|  
|スコープ|エッジ|  
|バージョン|4.6|  
|型|再ターゲット中|  
|影響を受ける API|<xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.Web.UI.HtmlTextWriterTag%29?displayProperty=fullName>|  
|アナライザー|CD0101|  
  
<a name="diagnostic104"></a>   
## <a name="104-calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>104: 項目が選択されている WPF ListBox、ListView、または DataGrid に対して Items.Refresh を呼び出すと、重複した項目が要素に表示される事があります。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.5 では、ListBox で項目が選択されているときにコードから ListBox.Items.Refresh を呼び出すと、選択された項目が一覧内に複製されます。 ListView と DataGrid でも、同様の問題が発生します。 これは、.NET Framework 4.6 で修正されます。|  
|提案される解決策|この問題は、Refresh が呼び出される前に、プログラムで項目を選択解除して、呼び出しの完了後に再び選択することによって回避できます。 または、この問題は .NET Framework 4.6 で修正されたため、このバージョンの .NET Framework にアップグレードすることによって対処できます。|  
|スコープ|マイナー|  
|バージョン|4.5-4.6|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Windows.Data.CollectionView.Refresh?displayProperty=fullName>|  
|アナライザー|CD0104|  
  
<a name="diagnostic105"></a>   
## <a name="105-etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>105: ETW EventListeners は、明示的なキーワードを持つプロバイダーからのイベント (TPL プロバイダーなど) をキャプチャしません。  
  
|||  
|-|-|  
|詳細|空白のキーワード マスクを持つ ETW EventListeners は、明示的なキーワードを持つプロバイダーからのイベントを正しくキャプチャしません。 .NET Framework 4.5 では、TPL プロバイダーは、明示的なキーワードを提供するようになり、この問題が発生しました。 .NET Framework 4.6 では、EventListeners が更新され、この問題は修正されました。|  
|提案される解決策|この問題を回避するには、EnableEvents(eventSource, level) の呼び出しを、使用する "any keywords" マスクを明示的に指定する EnableEvents オーバーロードの呼び出し (`EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))`) に置き換えます。<br /><br /> または、この問題は .NET Framework 4.6 で修正されたため、このバージョンの .NET Framework にアップグレードすることによって対処できます。|  
|スコープ|エッジ|  
|バージョン|4.5-4.6|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%29?displayProperty=fullName>|  
|アナライザー|CD0105|  
  
<a name="diagnostic109"></a>   
## <a name="109-building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>109: Visual Studio 2013 で Entity Framework edmx をビルドすると、EntityDeploySplit または EntityClean タスクを使用している場合、エラー MSB4062 で失敗することがあります。  
  
|||  
|-|-|  
|詳細|MSBuild 12.0 ツール (Visual Studio 2013 に含まれる) は、msbuild ファイルの位置を変更したため、古い Entity Framework のターゲット ファイルは無効になります。 その結果、`EntityDeploySplit` および `EntityClean` タスクは、`Microsoft.Data.Entity.Build.Tasks.dll` を見つけられないために失敗します。 この障害は、ツールセット (msbuild/VS) の変更によるものであり、.NET Framework の変更によるものではないことに注意してください。 開発者ツールをアップグレードしたときにのみ発生し、.NET Framework をアップグレード下だけでは発生しません。|  
|提案される解決策|Entity Framework のターゲット ファイルは、.NET Framework 4.6 以降の新しい msbuild レイアウトで機能するように修正されます。 このバージョンの Framework にアップグレードすることで、この問題は修正されます。 または、[この](http://stackoverflow.com/a/24249247/131944) 回避策を使用して、ターゲット ファイルに直接パッチを当てることができます。|  
|スコープ|Major|  
|バージョン|4.5.1-4.6|  
|型|再ターゲット中|  
|アナライザー|CD0109|  
  
<a name="diagnostic111"></a>   
## <a name="111-xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a>111: XSD スキーマ検証は、複合キーが使用され、1 つのキーが空の場合に、一意制約の違反を正しく検出するようになりました。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.6 より前のバージョンには、キーの 1 つが空であった場合、XSD 検証で複合キーの一意制約が検出されないというバグがありました。 .NET Framework 4.6 で、この問題は修正されました。 このため、より正しい検証が行われるようになりますが、以前は検証されていた XML の一部が検証されない可能性もあります。|  
|提案される解決策|より緩やかな .NET Framework 4.0 の検証が必要な場合、検証アプリケーションはバージョン 4.5 (またはそれ以前) の .NET Framework をターゲットにできます。 ただし、.NET 4.6 に再ターゲットするときには、コード レビューを行って、重複する複合キー (この問題の説明で述べられているように) の検証を予期していないことを確認する必要があります。|  
|スコープ|エッジ|  
|バージョン|4.6|  
|型|再ターゲット中|  
|アナライザー|CD0111|  
  
<a name="diagnostic112"></a>   
## <a name="112-calling-attributegetcustomattributes-on-an-indexer-property-no-longer-throws-ambiguousmatchexception-if-the-ambiguity-can-be-resolved-by-indexs-type"></a>112: インデクサ― プロパティに対して Attribute.GetCustomAttributes を呼び出しても、インデックスの型によって、あいまいさを解決できる場合、AmbiguousMatchException はスローされなくなりました。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.6 より以前には、インデックスの型のみが別のプロパティと異なるインデクサ― プロパティに対して `GetCustomAttribute(s)` を呼び出すと、`AmbiguousMatchException` になりました。 .NET Framework 4.6 からは、プロパティの属性が正しく返されます。|  
|提案される解決策|GetCustomAttribute(s) が、より頻繁に機能するようになったことに注意してください。 アプリが `AmbiguousMatchException` に依存していた場合は、代わりにリフレクションを使用して、複数のインデクサーを明示的に検索する必要があります。|  
|スコープ|エッジ|  
|バージョン|4.6|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Attribute.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%60%601%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%60%601%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%60%601%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%60%601%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName>|  
|アナライザー|CD0112|  
  
<a name="diagnostic113"></a>   
## <a name="113-intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a>113: カスタム Datatemplate を使用しているとき、断続的に、ItemsControls (ListBox や DataGrid など) 内の最後の項目までスクロールできません。  
  
|||  
|-|-|  
|詳細|場合によっては、.NET Framework 4.5 のバグにより、カスタム Datatemplate を使用していると、ItemsControls (ListBox、ComboBox、DataGrid など) の最後の項目までスクロールできません。 (上へスクロールした後で) もう一度スクロールを試みると、今度はスクロールできます。|  
|提案される解決策|この問題は .NET Framework 4.5.2 で修正されたため、このバージョン (またはそれ以降のバージョン) の .NET Framework にアップグレードすることによって対処できます。 または、ユーザーは、スクロール バーをこれらのコレクションの最後の項目までドラッグできますが、2 回試みなければならないことがあります。|  
|スコープ|マイナー|  
|バージョン|4.5-4.5.2|  
|型|ランタイム|  
|アナライザー|CD0113|  
  
<a name="diagnostic114"></a>   
## <a name="114-glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-45"></a>114: GlyphRun.ComputeInkBoundingBox() と FormattedText.Extent は、.NET 4.5 以降では、異なる値を返します。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.5 では、GlyphRun.ComputeInkBoundingBox() と FormattedText.Extent に改善が加えられ、.NET Framework 4.0 では、場合によっては、含まれるグリフに対してボックスが小さすぎるという問題に対応しました。 この結果、.NET Framework 4.5 以降では、いくつかの境界ボックスが大きくなり、UI のレイアウトにわずかな違いが生じます。|  
|提案される解決策|いくつかのグリフの境界ボックスのサイズが大きくなったことに注意してください。 このような変更は、通常、プレゼンテーションおよびヒット ボックス テストを向上させますが、以前の (.NET 4.5 より前の) 動作が望ましい場合は、次のエントリをアプリの構成ファイルに追加することによって実現できます。<br /><br /> `<appsettings> <add key="IncludeAllInkInBoundingBox" value="false"> </appsettings>`|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=fullName><br /><br /> <xref:System.Windows.Media.FormattedText.Extent?displayProperty=fullName>|  
|アナライザー|CD0114|  
  
<a name="diagnostic124"></a>   
## <a name="124-calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>124: CellEditEnding ハンドラーから DataGrid.CommitEdit を呼び出すと、フォーカスが削除されます。  
  
|||  
|-|-|  
|詳細|DataGrid の CellEditEnding イベント ハンドラーの 1 つから DataGrid.CommitEdit を呼び出すと、DataGrid からフォーカスが失われます。|  
|提案される解決策|このバグは .NET framework 4.5.2 で修正されたため、.NET Framework をアップグレードすることによって回避できます。 または、CommitEdit を呼び出した後で DataGrid を明示的に再選択することによって回避できます。|  
|スコープ|エッジ|  
|バージョン|4.5-4.5.2|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName><br /><br /> <xref:System.Windows.Controls.DataGrid.CommitEdit%28System.Windows.Controls.DataGridEditingUnit%2CSystem.Boolean%29?displayProperty=fullName>|  
|アナライザー|CD0124|  
  
<a name="diagnostic125"></a>   
## <a name="125-aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>125: ASP.NET MVC は、ルート パラメーターで渡された文字列内のスペースをエスケープするようになりました。  
  
|||  
|-|-|  
|詳細|RFC 2396 に準拠するために、ルートからアクション パラメーターを設定するときに、ルートのパスに含まれるスペースがエスケープされるようになりました。 そのため、`/controller/action/some data` は以前はルート `/controller/action/{data}` し、`some data` をデータ パラメーターとして与えましたが、代わりに `some%20data` を与えるようになります。|  
|提案される解決策|ルートからの文字列パラメーターをエスケープ解除するように、コードを更新する必要があります。 元の URI が必要な場合は、Request.RequestUri.OriginalString API でアクセスできます。|  
|スコープ|マイナー|  
|バージョン|4.5.2|  
|型|ランタイム|  
|影響を受ける API|[System.Web.Http.RouteAttribute](https://msdn.microsoft.com/library/system.web.http.routeattribute(v=vs.118).aspx)|  
|アナライザー|CD0125|  
  
<a name="diagnostic127"></a>   
## <a name="127-vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>127: VB.NET は、System.Windows Api の部分的な名前空間の修飾をサポートしなくなりました。  
  
|||  
|-|-|  
|詳細|.NET 4.5.2 以降では、VB.NET プロジェクトは、部分的に修飾された名前空間で System.Windows API を指定できません。 たとえば、`Windows.Forms.DialogResult` の参照は失敗します。 代わりに、コードは、完全修飾名 (`System.Windows.Forms.DialogResult`) を参照するか、特定の名前空間をインポートして、`DialogResult` を参照する必要があります。|  
|提案される解決策|`System.Windows` API を単純な名前で参照するか (および関連する名前空間をインポートする)、完全修飾名で参照するように、コードを更新する必要があります。|  
|スコープ|マイナー|  
|バージョン|4.5.2|  
|型|再ターゲット中|  
|アナライザー|CD0127|  
  
<a name="diagnostic129"></a>   
## <a name="129-two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a>129: 非パブリック セッターを持つプロパティへの双方向データ バインドはサポートされません。  
  
|||  
|-|-|  
|詳細|パブリック セッターを持たないプロパティへのデータ バインドを試みることは、サポートされるシナリオではありません。 .NET framework 4.5.1 以降では、このシナリオでは InvalidOperationException がスローされます。 この新しい例外は、具体的に .NET Framework 4.5.1 を対象とするアプリでのみスローされることに注意してください。 アプリが .NET Framework 4.5 をターゲットとしている場合、この呼び出しは許されます。 アプリが特定のバージョンの .NET Framework をターゲットにしていない場合、バインドは一方向として扱われます。|  
|提案される解決策|一方向のバインドを使用するか、プロパティのセッターを公開するように、アプリを更新する必要があります。 または、.NET Framework 4.5 をターゲットにすると、アプリは以前の動作を示すようになります。|  
|スコープ|マイナー|  
|バージョン|4.5.1|  
|型|再ターゲット中|  
|影響を受ける API|<xref:System.Windows.Data.BindingMode?displayProperty=fullName>|  
|アナライザー|CD0129|  
  
<a name="diagnostic130"></a>   
## <a name="130-marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>130: Marshal.SizeOf および Marshal.PtrToStructure オーバー ロードは、ダイナミック コードを中断します。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.5.1 以降では、メソッド `Marshal.SizeOf` または `Marshal.PtrToStructure` への動的なバインド (たとえば、Windows PowerShell、IronPython、または C# のダイナミック キーワードを使用して) を行うと、これらのメソッドの新しいオーバーロードが追加され、スクリプト エンジンにとってあいまいなことがあるため、`MethodInvocationExceptions` になります。|  
|提案される解決策|使用するオーバーロードを明確に示すように、スクリプトを更新します。 これは、一般に、メソッドの型パラメーターを `System.Type` として明示的にキャストすることによって行われます。 この問題の回避方法の詳細と例については、[このリンク](https://support.microsoft.com/kb/2909958/) を参照してください。|  
|スコープ|マイナー|  
|バージョン|4.5.1|  
|型|ランタイム|  
|アナライザー|CD0130|  
  
<a name="diagnostic131"></a>   
## <a name="131-previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a>131: PreviewLostKeyboardFocus は、そのハンドラーが Windows フォーム メッセージ ボックスを表示する場合、繰り返し呼び出されます。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.5 以降では、`UIElement.PreviewLostKeyboardFocus` ハンドラーから `System.Windows.Forms.MessageBox.Show` を呼び出すと、メッセージ ボックスが閉じられたとき、ハンドラーが再実行して、メッセージ ボックスの無限ループになる可能性があります。|  
|提案される解決策|この問題を回避するには、2 つの方法があります。<br /><br /> `System.Windows.Forms.MessageBox.Show` の代わりに `System.Windows.MessageBox.Show` を呼び出すことによって回避できます。<br /><br /> `LostKeyboardFocus` イベント ハンドラーから (`PreviewLostKeyboardFocus` イベント ハンドラーではなく) メッセージ ボックスを表示することによって回避できます。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=fullName><br /><br /> <xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=fullName><br /><br /> <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName><br /><br /> <xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=fullName>|  
|アナライザー|CD0131|  
  
<a name="diagnostic133"></a>   
## <a name="133-a-concurrentdictionary-serialized-in-net-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-451-or-452"></a>133: NetDataContractSerializer で .NET 4.5 でシリアル化された ConcurrentDictionary は、.NET 4.5.1 または 4.5.2 で逆シリアル化することはできません。  
  
|||  
|-|-|  
|詳細|型の内部変更により、.NET Framework 4.5 で `NetDataContractSerializer` を使用してシリアル化された `System.Collections.Concurrent.ConcurrentDictionary` オブジェクトは、.NET framework 4.5.2 または .NET Framework 4.5.1 で逆シリアル化することはできません。<br /><br /> 逆方向の移動 (.NET Framework 4.5.x でシリアル化して、.NET Framework 4.5 で逆シリアル化) は機能することに注意してください。 同様に、すべての 4.x バージョン間のシリアル化は、.NET Framework 4.6 で機能します。<br /><br /> 1 つのバージョンの .NET Framework でのシリアル化と逆シリアル化は影響を受けません。|  
|提案される解決策|.NET Framework 4.5 と .NET Framework 4.5.1/4.5.2 の間で ConcurrentDictionary のシリアル化と逆シリアル化を行う必要がある場合は、NetDataContractSerializer の代わりに、DataContractSerializer または BinaryFormatter シリアライザーなど、代替のシリアライザーを使用してください。<br /><br /> または、この問題は .NET Framework 4.6 で修正されたため、このバージョンの .NET Framework にアップグレードすることによって解決できます。|  
|スコープ|マイナー|  
|バージョン|4.5.1-4.6|  
|型|ランタイム|  
|アナライザー|CD0133|  
  
<a name="diagnostic134"></a>   
## <a name="134-persian-calendar-now-uses-the-hijri-solar-algorithm"></a>134: ペルシャ暦は、イスラム暦の太陽アルゴリズムを使用するようになりました。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.6 以降では、PersianCalendar クラスは、イスラム暦の太陽アルゴリズムを使用します。 PersianCalendar と他のカレンダーの間で日付を変換すると、に変換すると、.NET Framework 4.6 以降では、1800 年より前か 2023 年 (グレゴリオ暦) よりも後の日付について、わずかに異なる結果になることがあります。<br /><br /> また、`PersianCalendar.MinSupportedDateTime` は `March 22, 0622 instead of March 21, 0622` になりました。|  
|提案される解決策|.NET 4.6 で PersianCalendar を使用するときには、一部の早い日付または遅い日付に若干の差が生じる場合があることに注意してください。 また、異なるバージョンの .NET Framework で実行する可能性のあるプロセス間で日付をシリアル化するときには、PersianCalendar の日付文字列として格納しないでください (これらの値が異なる場合があるため)。|  
|スコープ|マイナー|  
|バージョン|4.6|  
|型|ランタイム|  
|影響を受ける API|<xref:System.Globalization.PersianCalendar?displayProperty=fullName>|  
|アナライザー|CD0134|  
  
<a name="diagnostic138"></a>   
## <a name="138-calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>138: null 引数を指定した CreateDefaultAuthorizationContext の呼び出しが変更されました。  
  
|||  
|-|-|  
|詳細|null の authorizationPolicies 引数を指定した `CreateDefaultAuthorizationContext(IList<IAuthorizationPolicy>)` の呼び出しによって返される AuthorizationContext の実装が、.NET Framework 4.6 で変更されました。|  
|提案される解決策|まれに、カスタム認証を使用する WCF アプリの動作に違いが生じる可能性があります。 このような場合は、2 つの方法のいずれかで、以前の動作を復元できます。<br /><br /> 4.6 よりも前のバージョンの .NET Framework を対象とするようにアプリを再コンパイルする。 IIS でホストされるサービスの場合、\<httpRuntime targetFramework="x.x"/> 要素を使用して、以前のバージョンの .NET Framework を対象とする。<br /><br /> app.config ファイルの `<appSettings>` セクションに以下の行を追加します: `<add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />`|  
|スコープ|マイナー|  
|バージョン|4.6|  
|型|再ターゲット中|  
|影響を受ける API|<xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%28System.Collections.Generic.IList%7BSystem.IdentityModel.Policy.IAuthorizationPolicy%7D%29?displayProperty=fullName>|  
|アナライザー|CD0138|  
  
<a name="diagnostic141"></a>   
## <a name="141-wpf-treeviewitem-must-be-used-within-a-treeview"></a>141: WPF TreeViewItem は TreeView 内で使用する必要があります。  
  
|||  
|-|-|  
|詳細|TreeView の外部での TreeViewItem 要素の使用を制限する変更が 4.5 で導入されました。 これは、次のような条件で発生します。<br /><br /> TreeViewItem のビジュアルの親がパネルではありません。 (TreeView に対して生成された TreeViewItem は、親としてパネルを持ちます)<br /><br /> TreeViewItem は、リスト コントロール (ListBox、DataGrid、ListView など) の「項目ホスト」として機能する VirtualizingStackPanel の子孫です。 仮想化を有効にする必要はありません。<br /><br /> VirtualizingStackPanel は、項目のスクロールです (`ScrollUnit="Item"`)。<br /><br /> 誰かが要素 `v` をスクロールして表示させるために `VirtualizingStackPanel.MakeVisible(v)` を呼び出します。 これは、明示的に行うか、さまざまな方法で暗黙的に行うことができます。おそらく、最も一般的な方法は、`v` をクリックして、キーボードのフォーカスを与えることです。<br /><br /> `v` から VirtualizingStackPanel までのビジュアル親チェーンが TreeViewItem を通過します。<br /><br /> 言い換えると、これは、TreeViewItem が TreeView の外部で使用されるときに見られ、ユーザーは TreeViewItem の子孫をクリックして表示させます。 TreeViewItem にフォーカスを取得できる子孫がない場合、この問題は見られません。 これが該当する状況の例は、TreeViewItem が DataTemplate のルートであるときです。  この問題に遭遇したときには、WPF フレームワーク内で InvalidCastException が発生しています。|  
|提案される解決策|このための修正プログラムが使用可能になります。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|ランタイム|  
|アナライザー|CD0141|  
  
<a name="diagnostic143"></a>   
## <a name="143-x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>143: X509CertificateClaimSet.FindClaims は、すべての claimTypes を考慮します。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.6.1 を対象とするアプリでは、X509 クレーム セットが、SAN フィールドに複数の DNS エントリを含む証明書から初期化された場合、FindClaims メソッドは、claimType 引数とすべての DNS エントリとの照合を試みます。<br /><br /> 以前のバージョンの .NET Framework を対象とするアプリの場合、FindClaims メソッドは、claimType 引数と最後の DNS エントリとの照合のみを試みます。|  
|提案される解決策|この変更は、.NET Framework 4.6.1 を対象とするアプリケーションのみに影響します。 この変更は、[DisableMultipleDNSEntries](https://msdn.microsoft.com/library/mt620030%28v=vs.110%29.aspx) 互換性スイッチで無効にできます (または、4.6.1 より前を対象としている場合は、有効にできます)。|  
|スコープ|マイナー|  
|バージョン|4.6.1|  
|型|再ターゲット中|  
|影響を受ける API|<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%28System.String%2CSystem.String%29?displayProperty=fullName>|  
|アナライザー|CD0143|  
  
<a name="diagnostic144"></a>   
## <a name="144-applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>144: Application.FilterMessage は、IMessageFilter.PreFilterMessage の再入可能な実装についてスローしなくなりました。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.6.1 より前では、(Application.DoEvents も呼び出しているときに) AddMessageFilter または RemoveMessageFilter を呼び出した IMessageFilter.PreFilterMessage 付きで Application.FilterMessage を呼び出すと、IndexOutOfRangeException が発生しました。<br /><br /> .NET Framework 4.6.1 以降を対象とするアプリケーションでは、この例外がスローされなくなり、上述の再入可能フィルターを使用できます。|  
|提案される解決策|Application.FilterMessage が上述の再入可能な IMessageFilter.PreFilterMessage の動作についてスローしなくなったことに注意してください。 これは、.NET Framework 4.6.1 を対象とするアプリケーションのみに影響します。<br /><br /> .NET Framework 4.6.1 を対象とするアプリは、[DontSupportReentrantFilterMessage](https://msdn.microsoft.com/library/mt620032%28v=vs.110%29.aspx) 互換性スイッチを使用することによって、この変更を解除できます (または、以前の Framework を対象としているアプリは、変更を受け入れることができます)。|  
|スコープ|エッジ|  
|バージョン|4.6.1|  
|型|再ターゲット中|  
|影響を受ける API|<xref:System.Windows.Forms.Application.FilterMessage%28System.Windows.Forms.Message%40%29?displayProperty=fullName>|  
|アナライザー|CD0144|  
  
<a name="diagnostic145"></a>   
## <a name="145-currentculture-is-not-preserved-across-wpf-dispatcher-operations"></a>145: CurrentCulture は、複数の WPF ディスパッチャー操作にわたって維持されません。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.6 以降では、[Dispatcher](https://msdn.microsoft.com/library/system.windows.threading.dispatcher%28v=vs.110%29.aspx) 内で CurrentCulture または CurrentUICulture に加えられた変更は、そのディスパッチャー操作の終了時に失われます。 同様に、ディスパッチャー操作の外部で CurrentCulture または CurrentUICulture に加えられた変更は、その操作の実行時には反映されないことがあります。<br /><br /> 具体的に言うと、つまり、CurrentCulture および CurrentUICulture の変更は、WPF UI コールバックと WPF アプリケーション内の他のコードの間でフローされない場合があります。<br /><br /> これは、[ExecutionContext](https://msdn.microsoft.com/library/system.threading.executioncontext%28v=vs.110%29.aspx) の変更によるものであり、この変更により、.NET Framework 4.6 以降を対象とするアプリでは、CurrentCulture および CurrentUICulture は実行コンテキストに格納されます。 WPF ディスパッチャー操作は、操作を開始するために使用された実行コンテキストを格納して、操作が完了したときに、以前のコンテキストを復元します。 CurrentCulture と CurrentUICulture がそのコンテキストの一部になったため、ディスパッチャー操作内でそれらに加えられた変更は、操作の外部では保持されません。|  
|提案される解決策|この変更による影響を受けるアプリは、望ましい CurrentCulture または CurrentUICulture をフィールドに格納し、すべてのディスパッチャー操作の本体 (UI イベントのコールバック ハンドラーを含む) で、正しい CurrentCulture と CurrentUICulture が設定されていることを確認することによって回避できます。 または、この WPF の変更の元となっている ExecutionContext の変更は、.NET Framework 4.6 以降を対象とするアプリのみに影響するため、.NET Framework 4.5.2 を対象とすることによって、この問題を回避できます。|  
|スコープ|マイナー|  
|バージョン|4.6|  
|型|再ターゲット中|  
|アナライザー|CD0145|
