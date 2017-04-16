---
title: ".NET の互換性の診断 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e481270-b62a-4cb4-8dda-5b4c5b59d61d
caps.latest.revision: 7
author: "twsouthwick"
ms.author: "tasou"
manager: "wpickett"
caps.handback.revision: 7
---
# .NET の互換性の診断
.NET の互換性の診断は、.NET Framework のバージョン間のアプリケーション互換性の問題を識別できるように - の電源を Roslyn アナライザーです。 この一覧が含まれますがすべて使用可能なアナライザーのサブセットのみが、特定の移行に適用されます。 アナライザーは、どの問題が計画的な移行のためできるものだけが表面化が決まります。 問題が影響を受けるバージョンで分割するを参照してください:[アプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility.md)します。  
  
 各問題には、次の情報が含まれています。  
  
-   以前のバージョンからの変更点の説明です。  
  
-   候補は、変更が顧客に与える影響し、回避策が異なるバージョン間で互換性を保持するために使用できるかどうかの説明を示します。  
  
-   変更はどの程度重要な評価。 アプリケーションの互換性の問題は、次のように分類されます。  
  
    |||  
    |-|-|  
    |Major|多数のアプリに影響や、コードに大幅な変更が必要な重大な変更。|  
    |マイナー|少数のアプリに影響するか、またはコードの小さな修正が必要な変更。|  
    |エッジ ケース|珍しいことで非常に特定のシナリオでアプリに影響を与える変更。|  
    |透明|アプリケーションの開発者やユーザーに大きな影響をなしに変更されました。|  
  
-   バージョンは、変更先が表示される場合、フレームワークを示します。 一部の変更は元に戻さし、もが示されます。  
  
-   変更の種類:  
  
    |||  
    |-|-|  
    |再ターゲット中|変更は、新しいバージョンの .NET Framework を対象とする再コンパイルされるアプリに影響します。|  
    |ランタイム|変更は、既存のアプリを .NET Framework の以前のバージョンを対象とは、以降のバージョンでは実行に影響します。|  
  
-   影響を受ける API、存在する場合。  
  
-   使用可能な診断の Id  
  
<a name="diagnostic1"></a>   
## <a name="1-soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a>1: SoapFormatter には、ハッシュ テーブルが逆シリアル化できませんのような順序付けになるコレクション オブジェクト  
  
|||  
|-|-|  
|詳細|SoapFormatter では、オブジェクトが&1; つの .NET Framework のバージョンの異なるバージョンでは正常に逆シリアル化をシリアル化されることは保証されません。 具体的には、(ハッシュ テーブル) のような順序付けられたコレクションの中では、.NET 4.5 を備えた serialzied の場合と .NET 4.0 でこれらの型のオブジェクトは逆シリアル化されるように 4.0 と 4.5 間のメンバーが追加されます。 シリアル化されたデータがシリアル化して、同じバージョンの .NET Framework と逆シリアル化された場合の問題が発生しないことに注意してください。|  
|提案される解決策|SoapFormatter シリアル化は、BinaryFormatter シリアル化または .NET Framework の変更に対応できる NetDataContractSerialization に置き換える必要があります。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize%28System.IO.Stream%29?displayProperty=fullName><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize%28System.IO.Stream%2CSystem.Runtime.Remoting.Messaging.HeaderHandler%29?displayProperty=fullName><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize%28System.IO.Stream%2CSystem.Object%29?displayProperty=fullName><br /><br /> [SoapFormatter.Serialize (ストリーム オブジェクト、ヘッダー\<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize%28System.IO.Stream%2CSystem.Object%2CSystem.Runtime.Remoting.Messaging.Header%5B%5D%29?displayProperty=fullName>|  
|アナライザー|CD0001B<br /><br /> CD0001A|  
  
<a name="diagnostic3"></a>   
## <a name="3-wpf-datatemplate-elements-are-now-visible-to-uia"></a>3: WPF DataTemplate 要素が UIA に表示されます  
  
|||  
|-|-|  
|詳細|以前は、DataTemplate 要素は、UI オートメーションを使用する表示できませんでした。 4.5 以降では、UI オートメーションではこれらの要素が検出されます。 これは、多くの場合に便利ですが、DataTemplate 要素を含まないために UIA ツリーに依存するテストを中断することができます。|  
|提案される解決策|UI Auomation テストが必要になるこのアプリには、以前に非表示の DataTemplate 要素を含むために UIA ツリーのアカウントを更新します。 たとえば、互いの横にあるいくつかの要素を必要とするテストでは、以前非表示のために UIA 要素間の予想される必要がありますようになりました。 または、UIA 要素が必要なは、特定の数やインデックスに依存するテストが新しい値で更新します。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Windows.DataTemplate.%23ctor?displayProperty=fullName><br /><br /> <xref:System.Windows.DataTemplate.%23ctor%28System.Object%29?displayProperty=fullName>|  
|アナライザー|CD0003|  
  
<a name="diagnostic4"></a>   
## <a name="4-wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>4: WPF のテキスト ボックスが選択されているテキストでは、テキスト ボックスがアクティブでない場合、それぞれ異なる色が表示されます  
  
|||  
|-|-|  
|詳細|.NET 4.5、WPF のテキスト ボックス コントロールがアクティブでないときに (これにフォーカスがない)、選択したテキスト ボックスの内側には、コントロールがアクティブな場合に異なる色が表示されます。|  
|提案される解決策|設定前の (.NET 4.0) 動作を復元することがあります、 [FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported](https://msdn.microsoft.com/en-us/library/system.windows.frameworkcompatibilitypreferences.areinactiveselectionhighlightbrushkeyssupported\(v=vs.110\).aspx)プロパティを false にします。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Windows.Controls.TextBox?displayProperty=fullName>|  
|アナライザー|CD0004|  
  
<a name="diagnostic5"></a>   
## <a name="5-listtforeach-can-throw-exception-when-modifying-list-item"></a>5: List<>\>.リスト項目を変更するときに、ForEach は例外をスローできます。  
  
|||  
|-|-|  
|詳細|.NET 4.5 以降で、`List<T>.ForEach`列挙子、呼び出し元のコレクション内の要素が変更された場合、InvalidOperationException 例外がスローされます。 以前は、この例外はスローされませんが、競合する可能性があります。|  
|提案される解決策|理想的には、安全な操作ではないため、要素の列挙中にリストを変更しないでコードを修正する必要があります。 以前の動作に戻すには、ただし、アプリ可能性がありますターゲットを .NET 4.0。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|再ターゲット中|  
|影響を受ける Api|<xref:System.Collections.Generic.List%601.ForEach%28System.Action%7B%600%7D%29?displayProperty=fullName>|  
|アナライザー|CD0005|  
  
<a name="diagnostic6"></a>   
## <a name="6-systemuri-parsing-adheres-to-rfc-3987"></a>6: RFC 3987 に準拠して System.Uri 解析  
  
|||  
|-|-|  
|詳細|URI の解析は、.NET 4.5 でのいくつかの方法で変更されました。 ただし、これらの変更に .NET 4.5 を対象としたコードのみに影響することに注意してください。 バイナリ対象 .NET 4.0 以前の動作が実行されます。 .NET 4.5 で URI の解析中の変更は次のとおりです。<br /><br /> URI 解析が正規化と文字の RFC 3987 の最新の IRI 規則に従ってチェックを実行します。<br /><br /> Unicode 正規形 C は、URI のホスト部分でのみ実行されます。<br /><br /> 無効な mailto: Uri は、例外が発生するようになりました<br /><br /> パス セグメントの最後に末尾のドットが保存されるよう<br /><br /> `file://`Uri がエスケープしない、`?`文字<br /><br /> Unicode 制御文字`U+0080`を通じて`U+009F`はサポートされていません<br /><br /> コンマ文字`,`または`%2c`は自動的にエスケープ解除されません|  
|提案される解決策|古い .NET 4.0 URI 解析セマンティクスが多くの場合は) 必要な場合は、.NET 4.0 を対象として使用できます。 これは、TargetFrameworkAttribute またはを使用して、アセンブリでは、[プロジェクトのプロパティ] ページの Visual Studio のプロジェクト システム UI によって実現できます。|  
|スコープ|Major|  
|バージョン|4.5|  
|型|再ターゲット中|  
|影響を受ける Api|<xref:System.Uri.%23ctor%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29?displayProperty=fullName><br /><br /> <xref:System.Uri.%23ctor%28System.Uri%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.TryCreate%28System.String%2CSystem.UriKind%2CSystem.Uri%40%29?displayProperty=fullName><br /><br /> <xref:System.Uri.TryCreate%28System.Uri%2CSystem.String%2CSystem.Uri%40%29?displayProperty=fullName><br /><br /> <xref:System.Uri.TryCreate%28System.Uri%2CSystem.Uri%2CSystem.Uri%40%29?displayProperty=fullName>|  
|アナライザー|CD0006D<br /><br /> CD0006C<br /><br /> CD0006F<br /><br /> CD0006E<br /><br /> CD0006A<br /><br /> CD0006G<br /><br /> CD0006B|  
  
<a name="diagnostic10"></a>   
## <a name="10-systemuri-escaping-now-supports-rfc-3986-httptoolsietforghtmlrfc3986"></a>10: System.Uri エスケープ RFC 3986 (http://tools.ietf.org/html/rfc3986) ようになりました  
  
|||  
|-|-|  
|詳細|URI のエスケープがサポートするために .NET 4.5 で変更された[RFC 3986](http://tools.ietf.org/html/rfc3986)します。 特定の変更は次のとおりです。<br /><br /> `EscapeDataString` は、予約されている文字を RFC 3986 に基づいてエスケープします。<br /><br /> `EscapeUriString` は、予約されている文字をエスケープしません。<br /><br /> `UnescapeDataString` は、無効なエスケープ シーケンスが発生した場合に例外をスローしません。<br /><br /> 予約されていないエスケープ文字はエスケープ解除されます。|  
|提案される解決策|無効なエスケープ シーケンスの場合にスローする UnescapeDataString に依存しないアプリケーションを更新します。 このようなシーケンスする必要がありますが認識される直接します。<br /><br /> 同様に、Escaped とエスケープ解除された URI、およびデータの文字列が .NET 4.0 および .NET 4.5 で異なる場合があり、.NET のバージョン間で、直接は比較されませんを期待してください。 代わりに、解析して、比較が行われる前に、1 つの .NET バージョンで正規化します。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Uri.EscapeDataString%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.EscapeUriString%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.UnescapeDataString%28System.String%29?displayProperty=fullName>|  
|アナライザー|CD0010A<br /><br /> CD0010B<br /><br /> CD0010C|  
  
<a name="diagnostic11"></a>   
## <a name="11-systemnetpeertopeercollaboration-unavailable-on-windows-8"></a>11: System.Net.PeerToPeer.Collaboration Windows 8 で使用できなくなった  
  
|||  
|-|-|  
|詳細|System.Net.PeerToPeer.Collaboration 名前空間は、Windows 8 またはそれ以降には使用できません。|  
|提案される解決策|Windows 8 をサポートするか、上、この名前空間またはそのメンバーに依存しないに更新する必要があるアプリ。|  
|スコープ|Major|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Net.PeerToPeer.Collaboration?displayProperty=fullName>|  
|アナライザー|CD0011|  
  
<a name="diagnostic12"></a>   
## <a name="12-mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>12: MEF カタログは、IEnumerable を実装しが不要になったため、シリアライザーを作成  
  
|||  
|-|-|  
|詳細|以降、.NET Framework 4.5 では、MEF カタログは IEnumerable を実装しは不要になったため、シリアライザー (XmlSerializer オブジェクト) を作成します。 MEF カタログをシリアル化しようとすると、例外がスローされます。|  
|提案される解決策|シリアライザーの作成に MEF を使用しないことができます。|  
|スコープ|Major|  
|バージョン|4.5|  
|型|ランタイム|  
|アナライザー|CD0012|  
  
<a name="diagnostic13"></a>   
## <a name="13-missing-target-framework-moniker-results-in-40-behavior"></a>13: ターゲット フレームワーク モニカーのない 4.0 の動作になります  
  
|||  
|-|-|  
|詳細|アプリケーションは、せず、 [TargetFrameworkAttribute](https://msdn.microsoft.com/en-us/library/system.runtime.versioning.targetframeworkattribute\(v=vs.110\).aspx)アセンブリ レベルで自動的に実行されます (quirks) の .NET Framework 4.0 のセマンティクスを使用して適用します。 高品質の確保、するバイナリはすべて明示的に属性を設定すると、ビルドされた .NET Framework のバージョンを示す TargetFrameworkAttribute をお勧めします。 Caues、TargetFrameworkAttribute を自動的に適用するために MSBuild をプロジェクト ファイルで、ターゲット フレームワーク モニカーを使用することに注意してください。|  
|提案される解決策|A[ターゲット フレームワーク属性](https://msdn.microsoft.com/en-us/library/system.runtime.versioning.targetframeworkattribute\(v=vs.110\).aspx)のいずれかによって、直接アセンブリまたはでターゲット フレームワークを指定することによって、属性を追加することを指定する必要があります、[プロジェクト ファイルまたは Visual Studio でプロジェクトのプロパティの GUI](http://blogs.msdn.com/b/visualstudio/archive/2010/05/19/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework.aspx)します。|  
|スコープ|Major|  
|バージョン|4.5|  
|型|ランタイム|  
|アナライザー|CD0013|  
  
<a name="diagnostic14"></a>   
## <a name="14-no-longer-able-to-set-enableviewstatemac-to-false"></a>14: EnableViewStateMac を false に設定することが不要になった  
  
|||  
|-|-|  
|詳細|ASP.NET でを指定する開発者は、不要になった`<pages enableViewStateMac="false"/>`または`<@Page EnableViewStateMac="false" %>`です。 ビュー ステートのメッセージ認証コード (MAC) は、ビュー ステートが埋め込まれたすべての要求に強制されています。 明示的に EnableViewStateMac プロパティを false に設定するだけのアプリが影響を受けます。|  
|提案される解決策|EnableViewStateMac は true に設定すると想定する必要があり、結果として得られる MAC エラーを解決する必要があります (で説明したよう[この](https://support.microsoft.com/en-us/kb/2915218)ガイダンスについては、MAC エラーの原因の詳細によって複数の解像度が含まれています)。|  
|スコープ|Major|  
|バージョン|4.5.2|  
|型|ランタイム|  
|アナライザー|CD0014|  
  
<a name="diagnostic18"></a>   
## <a name="18-blockingcollectionttrytakefromany-does-not-throw-anymore"></a>18: BlockingCollection<>\>します。TryTakeFromAny がもはやスローしません。  
  
|||  
|-|-|  
|詳細|入力コレクションの&1; つは、マークされている場合、完了した`BlockingCollection<T>.TryTakeFromAny(BlockingCollection<T>[], T)`-1 が返されなくと`BlockingCollection<T>.TakeFromAny`不要になった例外をスローします。 この変更の結果、コレクションの&1; つが空であったり完了していても、他のコレクションに取得できる項目がある場合にコレクションで作業をすることができるようになりました。|  
|提案される解決策|このようなコードを使用する変更ようになりました TryTakeFromAny-1 または TakeFromAny をスローすることを返す、完了しているときにブロッキング コレクションの場合、制御フローの目的で使用されていた場合`.Any(b => b.IsCompleted)`その状態を検出します。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|[BlockingCollection<>\>します。TakeFromAny (BlockingCollection<>\>\<xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%29?displayProperty=fullName><br /><br /> [BlockingCollection<>\>します。TakeFromAny (BlockingCollection<>\>\<xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> [BlockingCollection<>\>します。TryTakeFromAny (BlockingCollection<>\>\<xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%29?displayProperty=fullName><br /><br /> [BlockingCollection<>\>します。TryTakeFromAny (BlockingCollection<>\>\<xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%2CSystem.Int32%29?displayProperty=fullName><br /><br /> [BlockingCollection<>\>します。TryTakeFromAny (BlockingCollection<>\>\<xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%2CSystem.TimeSpan%29?displayProperty=fullName>|  
|アナライザー|CD0018A<br /><br /> CD0018B|  
  
<a name="diagnostic19"></a>   
## <a name="19-xmlschemaexception-now-sets-line-positions-properly"></a>19: XmlSchemaException セット位置を正しく整列するようになりました  
  
|||  
|-|-|  
|詳細|LoadOptions.SetLineInfo 値は、Load メソッドに渡される、検証エラーが発生した場合は、XmlSchemaException.LineNumber と XmlSchemaException.LinePosition プロパティが行情報には含まれています。|  
|提案される解決策|例外処理コード XmlSchemaException.LineNumber と XmlSchemaException.LinePosition が想定することはできませんので、これらのプロパティは今すぐを適切に設定 SetLineInfo を XML の読み込み中に使用する場合、セットを更新する必要があります。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Xml.Linq.LoadOptions?displayProperty=fullName>|  
|アナライザー|CD0019|  
  
<a name="diagnostic20"></a>   
## <a name="20-systemactivities-is-now-aptca"></a>20: System.Activities は APTCA はようになりました。  
  
|||  
|-|-|  
|詳細|アセンブリは、AllowPartiallyTrustedCallersAttribute 属性でマークされています。|  
|提案される解決策|派生クラスは、SecurityCriticalAttribute でマークすることはできません。 以前は、派生型は、SecurityCriticalAttribute でマークする必要があります。 ただし、この変更によって生じる実質的な影響はないはずです。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|アナライザー|CD0020|  
  
<a name="diagnostic21"></a>   
## <a name="21-workflow-30-types-are-obsolete"></a>21: 3.0 のワークフローの種類が廃止されています  
  
|||  
|-|-|  
|詳細|Windows Workflow Foundation (WWF) 3.0 Api (System.Workflow 名前空間のもの) は廃止されたようになりました。|  
|提案される解決策|新しい WWF 4.0 Api (System.Activities) は、代わりに使用する必要があります。 新しい Api を使用する例をご覧[ここ](https://msdn.microsoft.com/en-us/library/jj205427.aspx)ガイダンスについてはさらに、[ここ](http://blogs.msdn.com/b/workflowteam/archive/2012/02/08/deprecatingwf3.aspx)します。 または、WWF 3.0 Api がまだサポートされているは、使用される可能性はされ、それを抑制することによって、または以前のコンパイラを使用して、ビルド時に警告が回避されます。|  
|スコープ|Major|  
|バージョン|4.5|  
|型|再ターゲット中|  
|アナライザー|CD0021|  
  
<a name="diagnostic22"></a>   
## <a name="22-some-workflow-drag-and-drop-apis-are-obsolete"></a>22: 一部のワークフローのドラッグ アンド ドロップ Api が廃止されています  
  
|||  
|-|-|  
|詳細|このワークフローのドラッグ アンド ドロップ API は今後使用しませんし、4.5 に対して、アプリケーションが再構築する場合は、コンパイラの警告が発生します。|  
|提案される解決策|新しい[DragDropHelper](https://msdn.microsoft.com/en-us/library/system.activities.presentation.dragdrophelper\(v=vs.110\).aspx)複数のオブジェクトで操作をサポートする Api を代わりに使用する必要があります。 または、ビルド警告を抑制するか、古いコンパイラを使用してそれらを回避できます。 Api は引き続きサポートされます。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|再ターゲット中|  
|影響を受ける Api|<xref:System.Activities.Presentation.DragDropHelper.DoDragMove%28System.Activities.Presentation.WorkflowViewElement%2CSystem.Windows.Point%29?displayProperty=fullName><br /><br /> <xref:System.Activities.Presentation.DragDropHelper.GetCompositeView%28System.Windows.DragEventArgs%29?displayProperty=fullName><br /><br /> <xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem%28System.Windows.DragEventArgs%29?displayProperty=fullName><br /><br /> <xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject%28System.Windows.DependencyObject%2CSystem.Windows.DragEventArgs%2CSystem.Activities.Presentation.EditingContext%29?displayProperty=fullName>|  
|アナライザー|CD0022|  
  
<a name="diagnostic23"></a>   
## <a name="23-new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a>23: 新しい (あいまい) Dispatcher.Invoke オーバー ロードは、異なる動作になる可能性があります  
  
|||  
|-|-|  
|詳細|.NET Framework 4.5 では、System.Action 型のパラメーターを含む Dispatcher.Invoke に新しいオーバー ロードを追加します。 既存のコードを再コンパイルすると、コンパイラは、デリゲートのパラメーターを持つ System.Action パラメーターを持つ Dispatcher.Invoke メソッドへの呼び出しとして Dispatcher.Invoke メソッドの呼び出しを解決します。 デリゲートのパラメーターを持つ Dispatcher.Invoke オーバー ロードの呼び出しが System.Action パラメーターを持つ Dispatcher.Invoke オーバー ロードの呼び出しとして解決されると動作に次の違いが発生します。<br /><br /> 例外が発生する場合、Dispatcher.UnhandledExceptionFilter と Dispatcher.UnhandledException イベントは発生しません。 代わりに、例外は、UnobservedTaskException イベントによって処理されます。<br /><br /> DispatcherOperation.Result などの一部のメンバーへの呼び出しは、操作が完了するまでブロックします。|  
|提案される解決策|呼び出し元の Dispatcher.Invoke をコードではあいまいさ (および考えられる相違点の処理動作をブロックまたは例外) を渡すことが空のオブジェクトの 2 番目のパラメーターとして、.NET 4.0 メソッドのオーバー ロードに解決されるように、呼び出し。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|再ターゲット中|  
|影響を受ける Api|[Dispatcher.Invoke (委任、オブジェクトで\<xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> [Dispatcher.Invoke (デリゲート、TimeSpan、オブジェクト\<xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.TimeSpan%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> [Dispatcher.Invoke (オブジェクトの代理人、TimeSpan、dispatcherpriority および、\<xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.TimeSpan%2CSystem.Windows.Threading.DispatcherPriority%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> [Dispatcher.Invoke (デリゲート、dispatcherpriority および、オブジェクト\<xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.Windows.Threading.DispatcherPriority%2CSystem.Object%5B%5D%29?displayProperty=fullName>|  
|アナライザー|CD0023|  
  
<a name="diagnostic24"></a>   
## <a name="24-encoderparameter-ctor-is-obsolete"></a>24: EncoderParameter ctor は今後使用しません  
  
|||  
|-|-|  
|詳細|`EncoderParameter.EncoderParameter(Encoder, Int32, Int32, Int32)`コンス トラクターは廃止されましたと使用されている場合は、ビルドの警告が発生します。|  
|提案される解決策|ただし、`EncoderParameter.EncoderParameter(Encoder, Int32, Int32, Int32)`コンス トラクターは引き続き動作、次のコンス トラクターは .NET 4.5 のツールを使用してコードを再コンパイルするときに、古いビルド警告を回避する代わりに使用する必要があります: [EncoderParameter.EncoderParameter (エンコーダー、Int32、EncoderParameterValueType、IntPtr)](https://msdn.microsoft.com/en-us/library/hh875096\(v=vs.110\).aspx)します。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|再ターゲット中|  
|影響を受ける Api|<xref:System.Drawing.Imaging.EncoderParameter.%23ctor%28System.Drawing.Imaging.Encoder%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>|  
|アナライザー|CD0024|  
  
<a name="diagnostic26"></a>   
## <a name="26-change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a>26: Task.WaitAll メソッド タイムアウト引数を使用した場合の動作の変更  
  
|||  
|-|-|  
|詳細|Task.WaitAll 動作は、.NET 4.5 でより一貫性のある行われました。<br /><br /> .NET Framework 4 でこれらのメソッドは一貫性がない動作です。 1 つまたは複数のタスクが完了したか、メソッド呼び出しの前に取り消される場合、タイムアウトが期限切れ、メソッドには、AggregateException 例外がスローされました。 タイムアウトの期限が切れたタスクはありませんが完了またはメソッド呼び出しの前に取り消された&1; つまたは複数のタスクがこれらの状態、メソッドを呼び出した後、このメソッドが false 返されます。<br />.NET Framework 4.5 でこれらのメソッド オーバー ロード返すようになりましたされたタイムアウト期間の期限が切れて、(かどうか、メソッドの呼び出しの前後にでした) に関係なく、入力タスクが取り消されましたおよびその他のタスクがまだ実行されていない場合にのみ、AggregateException 例外をスローするときに、すべてのタスクが実行中の場合は false。|  
|提案される解決策|コードを IsCanceled プロパティを使用して同じ検出の実行で代わりに呼び出されている WaitAll 呼び出しの前にキャンセルされたタスクを検出するための手段として、AggregateException を受けたされている場合 (例: です。任意 (t t.IsCanceled =>))、タイムアウトする前に待機中のすべてのタスクが完了した場合、.NET 4.6 はその場合にスローのみためです。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|[Task.WaitAll (タスク\<xref:System.Threading.Tasks.Task.WaitAll%28System.Threading.Tasks.Task%5B%5D%2CSystem.Int32%29?displayProperty=fullName><br /><br /> [Task.WaitAll (タスク\<xref:System.Threading.Tasks.Task.WaitAll%28System.Threading.Tasks.Task%5B%5D%2CSystem.Int32%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> [Task.WaitAll (タスク\<xref:System.Threading.Tasks.Task.WaitAll%28System.Threading.Tasks.Task%5B%5D%2CSystem.TimeSpan%29?displayProperty=fullName>|  
|アナライザー|CD0026|  
  
<a name="diagnostic27"></a>   
## <a name="27-change-in-behavior-in-data-definition-language-ddl-apis"></a>27: データ定義言語 (DDL) の Api の動作の変更  
  
|||  
|-|-|  
|詳細|AttachDBFilename を指定すると、DDL Api の動作が次のように変更されました。<br /><br /> 接続文字列は、初期カタログ値を指定しなかった必要があります。 以前は、AttatchDBFilename と初期カタログの両方は必要でした。<br /><br /> AttatchDBFilename と初期カタログの両方が指定された所定の MDF ファイルが存在する場合は、ObjectContext.DatabaseExists メソッドは true を返します。 以前は、false 返されます。<br /><br /> AttatchDBFilename と初期カタログの両方が指定された所定の MDF ファイルが存在する場合、ObjectContext.DeleteDatabase メソッドを呼び出すと、ファイルが削除されます。<br /><br /> ObjectContext.DeleteDatabase は、接続文字列が存在しない MDF および、初期カタログが存在しないことを持つ AttachDBFilename の値を指定するときに呼び出されますが、メソッドは InvalidOperationException 例外をスローします。 以前は、SqlException 例外がスローされました。|  
|提案される解決策|これらの変更により、DDL API を使用するアプリケーションおよびツールの構築が簡単になりました。 これらの変更は、次のシナリオでアプリケーションの互換性に影響を及ぼす可能性があります。<br /><br /> ObjectContext.DatabaseExists true が返されます DROP DATABASE コマンドを呼び出し元の ObjectContext.DeleteDatabase ではなく直接実行するコードをユーザーが作成されます。 データベースがアタッチされておらず、MDF ファイルが存在する場合、これによって既存のコードが破損します。<br /><br /> ユーザーは、初期カタログと MDF ファイルが存在しない場合、InvalidOperationException 例外ではなく、SqlException 例外をスローする ObjectContext.DeleteDatabase メソッドを要求するコードを作成します。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|ランタイム|  
|アナライザー|CD0027|  
  
<a name="diagnostic28"></a>   
## <a name="28-machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a>28: MachineKey.Encode および MachineKey.Decode メソッドは、使用されなくなりました  
  
|||  
|-|-|  
|詳細|これらのメソッドは今後使用しません。 これらのメソッドを呼び出すコードをコンパイルすると、コンパイラ警告が生成されます。|  
|提案される解決策|推奨される代替手段は[MachineKey.Protect](https://msdn.microsoft.com/en-us/library/system.web.security.machinekey.protect\(v=vs.110\).aspx)と[MachineKey.Unprotect](https://msdn.microsoft.com/en-us/library/system.web.security.machinekey.unprotect\(v=vs.110\).aspx)します。 または、ビルド警告を抑制するか、古いコンパイラを使用してそれらを回避できます。 Api は引き続きサポートされます。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|再ターゲット中|  
|影響を受ける Api|<xref:System.Web.Security.MachineKey.Decode%28System.String%2CSystem.Web.Security.MachineKeyProtection%29?displayProperty=fullName><br /><br /> [MachineKey.Encode (バイト\<xref:System.Web.Security.MachineKey.Encode%28System.Byte%5B%5D%2CSystem.Web.Security.MachineKeyProtection%29?displayProperty=fullName>|  
|アナライザー|CD0028|  
  
<a name="diagnostic29"></a>   
## <a name="29-the-replace-method-in-odata-urls-is-disabled-by-default"></a>29: OData Url の置換メソッドが既定で無効になっています  
  
|||  
|-|-|  
|詳細|.NET Framework 4.5 以降では、OData Url の Replace メソッドは既定で無効にします。 (既定) は、OData の置換が無効である場合 (これは一般的ではない)、replace 関数を含むユーザーの要求は失敗します。|  
|提案される解決策|Replace メソッドが必要な場合 (これは通常ありません) を再度有効にできます、[構成設定を](https://msdn.microsoft.com/en-us/library/system.data.services.configuration.dataservicesfeaturessection.replacefunction.aspx)します。 ただし、有効になっている replace メソッドを使用して、セキュリティの脆弱性を開く、注意深くレビュー後でのみ使用する必要があります。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Data.Services.DataService%601?displayProperty=fullName>|  
|アナライザー|CD0029|  
  
<a name="diagnostic30"></a>   
## <a name="30-systemservicemodelwebwebservicehost-object-no-longer-adds-a-default-endpoint"></a>30: System.ServiceModel.Web.WebServiceHost オブジェクトが不要になったに既定のエンドポイントを追加  
  
|||  
|-|-|  
|詳細|System.ServiceModel.Web.WebServiceHost オブジェクトは、不要になったにはアプリケーション コードで明示的なエンドポイントが追加された場合、既定のエンドポイントの機能を追加します。|  
|提案される解決策|ユーザーは、既定のエンドポイントに接続できると期待して、他の明示的なエンドポイントは、WebServiceHost に追加されている場合は、既定のエンドポイントが明示的に追加も必要があります (AddDefaultEndpoints を使用)。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.ServiceModel.Description.ServiceEndpoint%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%2CSystem.Uri%29?displayProperty=fullName>|  
|アナライザー|CD0030A<br /><br /> CD0030B|  
  
<a name="diagnostic31"></a>   
## <a name="31-eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a>31: EventSource.WriteEvent impls WriteEvent 渡す必要があります (ID) および受け取った同じパラメーター  
  
|||  
|-|-|  
|詳細|ランタイムは、次を指定するコントラクトを強制するようになりました: ETW イベント メソッドを定義する EventSource から派生したクラスは、ETW イベント メソッドに渡された同じ引数が続くイベント ID を持つ EventSource.WriteEvent メソッドの基本クラスを呼び出す必要があります。|  
|提案される解決策|EventListener がこのコントラクトに違反するイベント ソースのプロセス内の EventSource データを読み取り、IndexOutOfRangeException 例外がスローされます。|  
|スコープ|マイナー|  
|バージョン|4.5.1|  
|型|ランタイム|  
|アナライザー|CD0031|  
  
<a name="diagnostic32"></a>   
## <a name="32-minfreememorypercentagetoactiveservice-is-now-respected"></a>32: MinFreeMemoryPercentageToActiveService が順守ようになりました  
  
|||  
|-|-|  
|詳細|WCF サービスをアクティブ化する前に、サーバーで使用する必要がある最小メモリを設定します。 OutOfMemoryException 例外を回避する設計します。 .NET Framework 4.5 では、この設定には効果はありません。 .NET Framework 4.5.1 で、設定を確認します。|  
|提案される解決策|Web サーバーで使用できる空きメモリが構成設定によって定義されたパーセンテージよりも小さい場合、例外が発生します。 制約されたメモリ環境で正常に開始し、実行された WCF サービスが今度は失敗することがあります。|  
|スコープ|マイナー|  
|バージョン|4.5.1|  
|型|ランタイム|  
|アナライザー|CD0032|  
  
<a name="diagnostic33"></a>   
## <a name="33-xmltextreader-dtd-entity-expansion-is-limited-to-10000000-characters"></a>33: XmlTextReader DTD エンティティの展開が 10,000, 000 文字に制限されます。  
  
|||  
|-|-|  
|詳細|DTD エンティティの展開が、10,000, 000 文字に制限されます。 DTD エンティティの展開を使用しない XML ファイルの読み込みや、制限された DTD エンティティの展開を使用した XML ファイルの読み込みは、影響を受けません。 DTD エンティティの展開が 10,000,000 文字を超えるファイルは読み込みに失敗し、例外をスローします。|  
|提案される解決策|値をオーバーライドできる DTD エンティティの展開の制限が低すぎる 10,000, 000 の場合、 [XmlReaderSettings.MaxCharactersFromEntities](https://msdn.microsoft.com/en-us/library/system.xml.xmlreadersettings.maxcharactersfromentities%28v=vs.110%29.aspx)プロパティです。 適切な MaxCharactersFromEntity 値を持つ、XmlReaderSettings を渡すことができる[XmlReader.Create](https://msdn.microsoft.com/en-us/library/System.Xml.XmlReader.Create\(v=vs.110\).aspx)|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Xml.XmlTextReader.%23ctor?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.Stream%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.Stream%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.Stream%2CSystem.Xml.XmlNodeType%2CSystem.Xml.XmlParserContext%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.TextReader%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.TextReader%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.Stream%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.Stream%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.TextReader%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.TextReader%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.Xml.XmlNodeType%2CSystem.Xml.XmlParserContext%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader?displayProperty=fullName>|  
|アナライザー|CD0033|  
  
<a name="diagnostic35"></a>   
## <a name="35-xslt-style-sheet-exception-message-changed"></a>35: XSLT スタイル シートの例外のメッセージの変更  
  
|||  
|-|-|  
|詳細|.NET Framework 4.5 では、XSLT ファイルが複雑すぎる場合のエラー メッセージのテキストは"、スタイル シートが複雑すぎます" 以前のバージョンのエラー メッセージは 「XSLT コンパイル エラー」でした。 エラー メッセージのテキストに依存するアプリケーション コードは機能しなくなります。 ただし、例外の種類、同じまま、この変更は実際の影響があるないためです。|  
|提案される解決策|このエラー状態から新しいメッセージを期待する excepton メッセージによってアプリケーション コードを更新しますか (さらに良い点) 例外の種類のみに依存するコードを更新 ([XsltException](https://msdn.microsoft.com/en-us/library/system.xml.xsl.xsltexception\(v=vs.110\).aspx))、これは変更されていません。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|[XslCompiledTransform.Load (MethodInfo、バイト\[\]、型\<xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Reflection.MethodInfo%2CSystem.Byte%5B%5D%2CSystem.Type%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.String%2CSystem.Xml.Xsl.XsltSettings%2CSystem.Xml.XmlResolver%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XPath.IXPathNavigable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XPath.IXPathNavigable%2CSystem.Xml.Xsl.XsltSettings%2CSystem.Xml.XmlResolver%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XmlReader%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XmlReader%2CSystem.Xml.Xsl.XsltSettings%2CSystem.Xml.XmlResolver%29?displayProperty=fullName>|  
|アナライザー|CD0035|  
  
<a name="diagnostic36"></a>   
## <a name="36-wf-serializes-expressionsliteralt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>36: WF Expressions.Literal をシリアル化<>\> DateTimes が異なるので (カスタム XAML パーサーを区切り)  
  
|||  
|-|-|  
|詳細|関連付けられた[ValueSerializer](https://msdn.microsoft.com/en-us/library/system.windows.markup.valueserializer\(v=vs.110\).aspx)オブジェクトは DateTime または DateTimeOffset オブジェクト変換、秒、ミリ秒のコンポーネントが含まれるが&0; 以外であり (DateTime の値) が DateTime.Kind プロパティは文字列ではなくプロパティ要素構文に指定されていない使用されません。 この変更は、ラウンドト リップする DateTime と DateTimeOffset の値を許可します。 入力 XAML が属性構文であると想定するカスタム XAML パーサーは正しく機能しません。|  
|提案される解決策|この変更は、ラウンドト リップする DateTime と DateTimeOffset の値を許可します。 入力 XAML が属性構文であると想定するカスタム XAML パーサーは正しく機能しません。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|アナライザー|CD0036|  
  
<a name="diagnostic37"></a>   
## <a name="37-new-enum-values-in-wpfs-pagerangeselection"></a>37: WPF の PageRangeSelection で新しい列挙値  
  
|||  
|-|-|  
|詳細|2 つの新しいメンバー (CurrentPage および SelectedPage) に追加された、 [PageRangeSelection](https://msdn.microsoft.com/en-us/library/system.windows.controls.pagerangeselection\(v=vs.110\).aspx)列挙型。|  
|提案される解決策|ほとんどの場合、これらの変更はユーザー コードに影響しません。 型変更する必要が、ただし PageRangeSelection で Enum.GetNames または Enum.GetValues で既存の要素の特定の数に依存するコードを呼び出します。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName>|  
|アナライザー|CD0037|  
  
<a name="diagnostic38"></a>   
## <a name="38-wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a>38: WPF DispatcherSynchronizationContext.CreateCopy が現在のインスタンスではなく新しいコピーを返すようになりました  
  
|||  
|-|-|  
|詳細|.NET Framework 4 で DispatcherSynchronizationContext.CreateCopy() には、パフォーマンスの最適化として、主に、現在のインスタンスへの参照が返されます。 .NET Framework 4.5 では、これにより、最初に等しい値の参照は、実行中のスレッドが正しく同期コンテキストで指定を完了するまでに新しいインスタンスを返します。  これらの参照の id をチェックするコードに影響は、.NET Framework 4.5 への移行の一部として変更されるため、DispatcherSynchronizationContext.CreateCopy を呼び出すコードをテストする必要がありますがありそうにない、またはそれ以降をお勧めします。|  
|提案される解決策|DispatcherSynchronizationContext.CreateCopy() は新しい SynchronizationContext オブジェクトを返すようになりましたことに注意してください。  以前は、このように生成された参照の等価性を使用するコードが実際に確認していませんかどうか、適切な状況でがに対して .NET 4.5 以降のビルド時に。  問題が発生するまれに、影響を受けるコード パスを使用することできるようこの場合の問題であるかどうかを判断します。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=fullName>|  
|アナライザー|CD0038|  
  
<a name="diagnostic39"></a>   
## <a name="39-systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a>39: System.Threading.Tasks.Task は、オブジェクトが破棄された後に不要になった ObjectDisposedException をスロー  
  
|||  
|-|-|  
|詳細|Task.IAsyncResult.AsyncWaitHandle、を除き System.Threading.Tasks.Task メソッドでは、オブジェクトが破棄された後に ObjectDisposedException 例外が不要になったスローします。<br />この変更により、キャッシュされたタスクを使用できるようになりました。 たとえば、メソッドで新しいタスクを割り当てる代わりに、既に完了した操作を表す、キャッシュされたタスクを返すことができます。 これは、タスクの任意のコンシューマーによって破棄されてしまうと、使用不可能になってしまう以前の .NET Framework のバージョンでは不可能でした。|  
|提案される解決策|タスク メソッドが不要になった ObjectDisposedExceptions 場合にスロー オブジェクトが破棄されるときに注意してください。 タスクのステータスを明示的にチェックする更新するか、アプリをタスクが破棄されたことを確認するには、この例外に依存していた場合を使用して[Task.Status](https://msdn.microsoft.com/en-us/library/system.threading.tasks.task.status\(v=vs.110\).aspx)します。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|ランタイム|  
|アナライザー|CD0039|  
  
<a name="diagnostic40"></a>   
## <a name="40-different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a>40: ObjectContext.CreateDatabase および DbProviderServices.CreateDatabase メソッドで処理する別の例外  
  
|||  
|-|-|  
|詳細|.NET 4.5 以降で、データベースの作成が失敗した場合、`CreateDatabase`メソッドは、空のデータベースを削除しようとしています。 その操作が成功すると、元の`SQLException`伝達されます (の代わりに、 `InvalidOperationException` .NET 4.0 でを常がスローされました)|  
|提案される解決策|ObjectContext.CreateDatabase または DbProviderServices.CreateDatabase 実行中に、InvalidOperationException をキャッチするときに SQLExceptions を今すぐもして捕捉されます。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Data.Common.DbProviderServices.CreateDatabase%28System.Data.Common.DbConnection%2CSystem.Nullable%7BSystem.Int32%7D%2CSystem.Data.Metadata.Edm.StoreItemCollection%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName>|  
|アナライザー|CD0040|  
  
<a name="diagnostic41"></a>   
## <a name="41-objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a>41: ObjectContext.Translate と ObjectContext.ExecuteStoreQuery 列挙型をサポート  
  
|||  
|-|-|  
|詳細|.NET 4.0 では、ジェネリック パラメーターで`T`の`ObjectContext.Translate`と`ObjectContext.ExecuteStoreQuery`メソッドを列挙できませんでした。 このシナリオはサポートされています。|  
|提案される解決策|.NET 4.0 で列挙型 翻訳 または ExecuteStoreQuery が呼び出される場合は、'0' が返されました。 動作をすることが望ましい場合は、定数 0 (またはその列挙型と同等) の呼び出しを置き換えてください。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|[ObjectContext.ExecuteStoreQuery<>\>(文字列, オブジェクト\<xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601%28System.String%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> [ObjectContext.ExecuteStoreQuery<>\>(オブジェクトの文字列、文字列、MergeOption、\<xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601%28System.String%2CSystem.String%2CSystem.Data.Objects.MergeOption%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.Translate%60%601%28System.Data.Common.DbDataReader%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.Translate%60%601%28System.Data.Common.DbDataReader%2CSystem.String%2CSystem.Data.Objects.MergeOption%29?displayProperty=fullName>|  
|アナライザー|CD0041|  
  
<a name="diagnostic42"></a>   
## <a name="42-enumerableemptytresult-always-returns-cached-instance"></a>42: Enumerable.Empty<> \</> \>常にインスタンスのキャッシュを返します  
  
|||  
|-|-|  
|詳細|.NET 4.5 以降で`Enumerable.Empty`常にキャッシュされた内部インスタンスを返します`IEnumerable<T>`します。<br /><br /> 以前は、 `Enumerable.Empty` 、空のキャッシュは`IEnumerable<T>`API が呼び出された時点で、つまりをいくつかの条件下で`Enumerable.Empty`が呼び出された迅速かつ同時に、さまざまな API の呼び出しを別の型のインスタンスを返す可能性があります。|  
|提案される解決策|以前の動作非確定的なので、コードが依存している可能性がありません。 ただし、ありそうにない場合は空の列挙を比較しているし、も等しくない場合に、明示的な空の配列を作成する (`new T[0]`) を使用せずに`Enumerable.Empty`します。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Linq.Enumerable.Empty%60%601?displayProperty=fullName>|  
|アナライザー|CD0042|  
  
<a name="diagnostic43"></a>   
## <a name="43-httprequestcontentencoding-property-prohibits-utf7"></a>43: HttpRequest.ContentEncoding プロパティには、UTF7 が禁止されています  
  
|||  
|-|-|  
|詳細|.NET Framework 4.5 以降は、utf-7 エンコードは禁止されています HttpRequests の本文にします。 UTF-7 データの受信を必要とするアプリケーションのデータが、正しくデコードされない場合があります。|  
|提案される解決策|理想的には、utf-7 は HttpRequests でエンコードを使用しないようにアプリケーションを更新する必要があります。 使用してレガシの動作を復元する代わりに、`aspnet:AllowUtf7RequestContentEncoding`の属性、 [appSettings](https://msdn.microsoft.com/en-us/library/hh975440\(v=vs.110\).aspx)要素。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Web.HttpRequest.ContentEncoding?displayProperty=fullName>|  
|アナライザー|CD0043|  
  
<a name="diagnostic44"></a>   
## <a name="44-httputilityjavascriptstringencode-escapes-ampersand"></a>44: HttpUtility.JavaScriptStringEncode アンパサンドをエスケープします。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.5 以降、JavaScriptStringEncode はアンパサンド (&) 文字をエスケープします。|  
|提案される解決策|アプリは、このメソッドの以前の動作に依存している場合は、aspnet:JavaScriptDoNotEncodeAmpersand 設定を追加することができます、 [ASP.NET appSettings 要素](https://msdn.microsoft.com/en-us/library/hh975440\(v=vs.110\).aspx)構成ファイルにします。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Web.HttpUtility.JavaScriptStringEncode%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Web.HttpUtility.JavaScriptStringEncode%28System.String%2CSystem.Boolean%29?displayProperty=fullName>|  
|アナライザー|CD0044A<br /><br /> CD0044B|  
  
<a name="diagnostic46"></a>   
## <a name="46-eventlistener-truncates-strings-with-embedded-nulls"></a>46: EventListener が埋め込まれた null のある文字列を切り捨てます  
  
|||  
|-|-|  
|詳細|EventListener には、埋め込まれた null のある文字列が切り詰められます。 EventSource クラスでは、null 文字はサポートされていません。 変更は、プロセスの EventSource データを読み取る EventListener を使用し、区切り記号として null 文字を使用するアプリにのみ影響します。|  
|提案される解決策|EventSource データを更新する、可能であれば、埋め込まれた null 文字を使用しないようにします。|  
|スコープ|エッジ|  
|バージョン|4.5.1|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Diagnostics.Tracing.EventListener.%23ctor?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%2CSystem.Diagnostics.Tracing.EventKeywords%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%2CSystem.Diagnostics.Tracing.EventKeywords%2CSystem.Collections.Generic.IDictionary%7BSystem.String%2CSystem.String%7D%29?displayProperty=fullName> \</String, String>|  
|アナライザー|CD0046|  
  
<a name="diagnostic48"></a>   
## <a name="48-obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a>48: ObsoleteAttribute WinMD のシナリオで ObsoleteAttribute と DeprecatedAttribute の両方としてエクスポートします。  
  
|||  
|-|-|  
|詳細|Windows メタデータ ライブラリ (.winmd ファイル) を作成するときに、ObsoleteAttribute 属性は ObsoleteAttribute と Windows.Foundation.DeprecatedAttribute の両方としてエクスポートされます。|  
|提案される解決策|ObsoleteAttribute 属性を使用する既存のソース コードの再コンパイルからそのコードを使用するときに警告が生成が/cli/CX または JavaScript。<br /><br /> お勧めしません。 管理対象のアセンブリのコードに ObsoleteAttribute と Windows.Foundation.DeprecatedAttribute の両方を適用します。ビルドの警告可能性があります。|  
|スコープ|エッジ|  
|バージョン|4.5.1|  
|型|再ターゲット中|  
|アナライザー|CD0048A<br /><br /> CD0048B|  
  
<a name="diagnostic49"></a>   
## <a name="49-resolveassemblyreference-task-now-warns-on-dependencies-with-the-wrong-architecture"></a>49: 今すぐ ResolveAssemblyReference タスクは間違ったアーキテクチャと依存関係に関する警告が表示されます  
  
|||  
|-|-|  
|詳細|タスクは警告 MSB3270 を生成します。これは参照または依存関係がアプリのアーキテクチャと一致しないことを示します。 たとえば、これが発生した [anycpu] オプションを使用してコンパイルされたアプリには、x86 が含まれている場合の参照。 このようなシナリオは、実行時にアプリでエラーが起こった場合に発生することがあります (この場合は、アプリが x64 プロセスとして配置されている場合)。|  
|提案される解決策|影響には&2; つの領域があります。<br /><br /> 再コンパイルすると、アプリが MSBuild の以前のバージョンでコンパイルされたときには現れなかった警告が生成されます。 ただし、警告はランタイム エラーの可能性のある原因を特定するため、調査と対処が必要です。<br /><br /> 警告がエラーとして扱われると、アプリはコンパイルされません。|  
|スコープ|マイナー|  
|バージョン|4.5.1|  
|型|再ターゲット中|  
|アナライザー|CD0049|  
  
<a name="diagnostic51"></a>   
## <a name="51-wpf-textbox-defaults-to-undo-limit-of-100"></a>51: WPF のテキスト ボックスの既定値の上限が 100 を元に戻す  
  
|||  
|-|-|  
|詳細|.NET 4.5 での WPF のテキスト ボックスの既定の元に戻す制限には、(.NET 4.0 の制限はありませんが) ではなく 100|  
|提案される解決策|テキスト ボックスの UndoLimit プロパティを使用して元に戻す制限の 100 が低すぎる場合は、制限値を明示的に設定できます。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Windows.Controls.TextBox?displayProperty=fullName>|  
|アナライザー|CD0051|  
  
<a name="diagnostic55"></a>   
## <a name="55-exceptions-during-unobserved-processing-in-systemthreadingtaskstask-no-longer-propagate-on-finalizer-thread"></a>55: System.Threading.Tasks.Task で観察されていない処理中に例外が不要になったファイナライザー スレッドに反映  
  
|||  
|-|-|  
|詳細|System.Threading.Tasks.Task クラスが非同期操作を表すために、非同期処理中に発生したすべての重大ではない例外をキャッチします。 .NET Framework 4.5 では、例外が確認されていないと、コードは、タスクが待機する場合、例外は、不要になったファイナライザー スレッドに反映し、ガベージ コレクション中に、プロセスがクラッシュします。 この変更は、タスク クラスを使用して観察されていない非同期処理を実行するアプリケーションの信頼性を向上します。|  
|提案される解決策|適切なハンドラーを提供することによって、以前の動作を復元できますアプリは、観察されない非同期例外がファイナライザー スレッドへの反映に依存している場合、 [TaskScheduler.UnobservedTaskException](https://msdn.microsoft.com/en-us/library/system.threading.tasks.taskscheduler.unobservedtaskexception\(v=vs.110\).aspx)イベントを設定したり、[ランタイムの構成要素](https://msdn.microsoft.com/en-us/library/jj160346%28v=vs.110%29.aspx)します。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Threading.Tasks.Task.Run%28System.Action%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%28System.Action%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%60%600%7D%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%60%600%7D%7D%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7B%60%600%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7B%60%600%7D%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Start?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Start%28System.Threading.Tasks.TaskScheduler%29?displayProperty=fullName>|  
|アナライザー|CD0055|  
  
<a name="diagnostic58"></a>   
## <a name="58-iasyncresultcompletedsynchronously-property-must-be-correct-for-the-resulting-task-to-complete"></a>58: IAsyncResult.CompletedSynchronously プロパティは、結果のタスクを完了するために適切である必要があります  
  
|||  
|-|-|  
|詳細|TaskFactory.FromAsync を呼び出すときに、IAsyncResult.CompletedSynchronously プロパティの実装は、結果のタスクを完了するために正しくなければなりません。 つまり、プロパティは、実装が同期的に完了した場合のみ、true を返す必要があります。 以前は、このプロパティは確認されていませんでした。|  
|提案される解決策|IAsyncResult の実装は正しく仕事が同期的に完了した場合にのみ、CompletedSynchronusly プロパティに true を返す場合、break は検出されません。 ユーザーは必要があります (存在する場合) を評価できるように正しく完了したか同期的に作業するかどうかを所有する IAsyncResult の実装を確認します。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|再ターゲット中|  
|影響を受ける Api|<xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Object%29?displayProperty=fullName> \</AsyncCallback, Object, IAsyncResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</AsyncCallback, Object, IAsyncResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.IAsyncResult%2CSystem.Action%7BSystem.IAsyncResult%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.IAsyncResult%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.IAsyncResult%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Threading.Tasks.TaskCreationOptions%2CSystem.Threading.Tasks.TaskScheduler%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Object%29?displayProperty=fullName> \</IAsyncResult, TResult> \</AsyncCallback, Object, IAsyncResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</IAsyncResult, TResult> \</AsyncCallback, Object, IAsyncResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2CSystem.Object%29?displayProperty=fullName> </TArg1, AsyncCallback, Object, IAsyncResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</TArg1, AsyncCallback, Object, IAsyncResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%29?displayProperty=fullName> \</IAsyncResult, TResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</IAsyncResult, TResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Threading.Tasks.TaskCreationOptions%2CSystem.Threading.Tasks.TaskScheduler%29?displayProperty=fullName> \</IAsyncResult, TResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%601%7D%2C%60%600%2CSystem.Object%29?displayProperty=fullName> \</IAsyncResult, TResult> \</TArg1, AsyncCallback, Object, IAsyncResult> \</TArg1, TResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%601%7D%2C%60%600%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</IAsyncResult, TResult> \</TArg1, AsyncCallback, Object, IAsyncResult> \</TArg1, TResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2CSystem.Object%29?displayProperty=fullName> </TArg1, TArg2, AsyncCallback, Object, IAsyncResult> </TArg1, TArg2><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</TArg1, TArg2, AsyncCallback, Object, IAsyncResult> \</TArg1, TArg2><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%602%7D%2C%60%600%2C%60%601%2CSystem.Object%29?displayProperty=fullName> \</IAsyncResult, TResult> \</TArg1, TArg2, AsyncCallback, Object, IAsyncResult> \</TArg1, TArg2, TResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%602%7D%2C%60%600%2C%60%601%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</IAsyncResult, TResult> \</TArg1, TArg2, AsyncCallback, Object, IAsyncResult> \</TArg1, TArg2, TResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%29?displayProperty=fullName> </TArg1, TArg2, TArg3, AsyncCallback, Object, IAsyncResult> </TArg1, TArg2, TArg3><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</TArg1, TArg2, TArg3, AsyncCallback, Object, IAsyncResult> \</TArg1, TArg2, TArg3><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%604%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%603%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%29?displayProperty=fullName> \</IAsyncResult, TResult> \</TArg1, TArg2, TArg3, AsyncCallback, Object, IAsyncResult> \</TArg1, TArg2, TArg3, TResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%604%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%603%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</IAsyncResult, TResult> \</TArg1, TArg2, TArg3, AsyncCallback, Object, IAsyncResult> \</TArg1, TArg2, TArg3, TResult>|  
|アナライザー|CD0058|  
  
<a name="diagnostic59"></a>   
## <a name="59-log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a>59: ObjectContext.CreateDatabase メソッドによって作成されたログ ファイル名が SQL Server の仕様に一致するように変更されました。  
  
|||  
|-|-|  
|詳細|CreateDatabase メソッドを直接呼び出してまたは SqlClient プロバイダーと接続文字列の AttachDBFilename の値が Code First を使用して、ログ ファイルを作成するときに、コマンドを実行し (ここで、ファイル名は AttachDBFilename の値で指定されたファイルの名前) ではなく filename_log.ldf がという名前です。 この変更により、SQL Server の仕様に従ってログ ファイル名が提供されるため、デバッグ機能が向上します。|  
|提案される解決策|ログ ファイルの名前がアプリケーションの重要な場合、アプリケーションが標準 _log.ldf ファイル名の形式が要求を更新する必要があります。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName>|  
|アナライザー|CD0059|  
  
<a name="diagnostic60"></a>   
## <a name="60-pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a>60: Page.LoadComplete イベントは、データ バインディングを呼び出す System.Web.UI.WebControls.EntityDataSource コントロールを不要になったにより  
  
|||  
|-|-|  
|詳細|`Page.LoadComplete`イベントが作成/更新/削除パラメーター変更を加えるのためのデータ バインディングを呼び出す System.Web.UI.WebControls.EntityDataSource コントロールを不要になったさせます。 この変更は、データベースへの不要なアクセスを排除、コントロールの値がリセットされることを防止し、SqlDataSource、ObjectDataSource などその他のデータ コントロールと一貫性のある動作を生成します。 この変更により、アプリケーションが `Page.LoadComplete` イベントのデータ バインディングの呼び出しに依存するような珍しい状況において、異なる動作が生成されるようになりました。|  
|提案される解決策|データ バインドの必要性がある場合は、ポストバックの前半であるイベントのデータ バインドを手動で起動します。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|アナライザー|CD0060|  
  
<a name="diagnostic61"></a>   
## <a name="61-webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a>61: WebUtility.HtmlDecode が不要になった無効な入力シーケンスをデコード  
  
|||  
|-|-|  
|詳細|既定では、デコード メソッドによって無効な入力シーケンスが無効な UTF-16 文字列にデコードされることがなくなりました。 代わりに、元の入力が返されます。|  
|提案される解決策|デコーダーの出力の変更は、UTF-16 データではなくバイナリ データを文字列に格納した場合にのみ影響があります。 この動作を明示的に制御する設定、`aspnet:AllowRelaxedUnicodeDecoding`の属性、 [appSettings](https://msdn.microsoft.com/en-us/library/ms228154\(v=vs.110\).aspx)レガシーの動作を有効にする場合は true または false に設定すると、現在の動作を有効にする要素。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Net.WebUtility.HtmlDecode%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Net.WebUtility.HtmlDecode%28System.String%2CSystem.IO.TextWriter%29?displayProperty=fullName><br /><br /> <xref:System.Net.WebUtility.UrlDecode%28System.String%29?displayProperty=fullName>|  
|アナライザー|CD0061|  
  
<a name="diagnostic63"></a>   
## <a name="63-apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>63: Windows 2003 で sha-256 コード署名証明書を使用する ClickOnce で発行されたアプリが失敗します。  
  
|||  
|-|-|  
|詳細|この実行可能ファイルは SHA256 で署名されます。 以前は、コード署名証明書が SHA-1 か SHA-256 に関係なく、SHA&1; で署名されました。 この方法は、次の対象に適用されます。<br /><br /> Visual Studio 2012 以降でビルドされたすべてのアプリケーション。<br /><br /> .NET Framework 4.5 がインストールされているシステム上で、Visual Studio 2010 以前でビルドされたアプリケーション。<br /><br /> さらに、.NET Framework 4.5 以降が存在する場合、コンパイル対象となった .NET Framework のバージョンに関係なく、ClickOnce マニフェストはSHA-256 証明書の SHA 256 で署名されます。|  
|提案される解決策|ClickOnce 実行可能ファイルの署名に変更が Windows Server 2003 システムだけです。これらは、サポート技術情報 938397 をインストールすることが必要です。<br /><br /> アプリが .NET Framework 4.0 以前のバージョンをターゲットとしている場合でも、SHA-256 を使用したマニフェストの署名方法の変更により、.NET Framework 4.5 以降のバージョンに対するランタイム依存関係が導入されます。|  
|スコープ|エッジ|  
|バージョン|4.5-4.6|  
|型|再ターゲット中|  
|アナライザー|CD0063|  
  
<a name="diagnostic68"></a>   
## <a name="68-dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a>68: DbParameter.Precision と DbParameter.Scale は、パブリックの仮想メンバー  
  
|||  
|-|-|  
|詳細|DbParameter.Precision と DbParameter.Scale は、パブリック仮想プロパティとして実装されます。 対応する明示的なインターフェイス実装、DbParameter.IDbDataParameter.Precision と DbParameter.IDbDataParameter.Scale 置き換えられます。|  
|提案される解決策|ADO.NET データベース プロバイダーを再構築する場合、これらの違いには、精度とスケールのプロパティに適用される 'override' キーワードが必要です。 これは必要になるだけです。 コンポーネントを再構築既存のバイナリは引き続き機能します。|  
|スコープ|マイナー|  
|バージョン|4.5.1|  
|型|再ターゲット中|  
|影響を受ける Api|<xref:System.Data.Common.DbParameter.Precision?displayProperty=fullName><br /><br /> <xref:System.Data.Common.DbParameter.Scale?displayProperty=fullName>|  
|アナライザー|CD0068|  
  
<a name="diagnostic73"></a>   
## <a name="73-dataobjectgetdata-now-retrieves-data-as-utf-8"></a>73: DataObject.GetData にデータを utf-8 として取得  
  
|||  
|-|-|  
|詳細|対象とする .NET Framework 4 または .NET Framework 4.5.1 以前のバージョンで実行されているアプリの場合は、DataObject.GetData は、HTML 形式のデータを ASCII 文字列として取得します。 結果として、非 ASCII 文字 (ASCII コードが 0x7F よりも大きい文字) は 2 つのランダムな文字で表されます。<br /><br /> .NET Framework 4.5 または以降に、.NET Framework 4.5.2、上で実行を対象とするアプリの`DataObject.GetData`0x7F よりも大きい文字を正しく表す utf-8 として HTML 形式のデータを取得します。|  
|提案される解決策|(たとえば、UTF8Encoding.GetString メソッドに渡すことによって、クリップボードから取得した HTML 文字列を明示的にエンコード) を HTML 形式の文字列を含むエンコーディングの問題に対する回避策を実装して、バージョン 4 から 4.5 へアプリを再ターゲットしている場合は、その回避策を削除してください。<br /><br /> 以前の動作は何らかの理由のために必要なアプリケーションはその動作を実現する .NET Framework 4.0 を対象することができます。|  
|スコープ|エッジ|  
|バージョン|4.5.2|  
|型|再ターゲット中|  
|影響を受ける Api|<xref:System.Windows.DataObject.GetData%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Windows.DataObject.GetData%28System.String%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Windows.DataObject.GetData%28System.Type%29?displayProperty=fullName>|  
|アナライザー|CD0073|  
  
<a name="diagnostic75"></a>   
## <a name="75-targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>75: 既定のアプリケーション ドメインの TargetFrameworkName 不要になった既定値は null に設定されていない場合  
  
|||  
|-|-|  
|詳細|TargetFrameworkName は、明示的に設定されている場合を除き、既定のアプリケーション ドメインで以前 null でした。 4.6 以降では、既定のアプリケーション ドメインの TargetFrameworkName プロパティは (ある場合)、TargetFrameworkAttribute から派生した既定値があります。 既定以外のアプリ ドメインが明示的にオーバーライドされない限り、既定のアプリケーション ドメイン (これは 4.6 で null が既定で) から、TargetFrameworkName を継承し続けます。|  
|提案される解決策|依存するコードを更新するか`AppDomainSetup.TargetFrameworkName`既定では null です。 必要な場合、このプロパティは null と評価を続けます、明示的に設定できますがその値にします。|  
|スコープ|エッジ|  
|バージョン|4.6|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName>|  
|アナライザー|CD0075B<br /><br /> CD0075A|  
  
<a name="diagnostic76"></a>   
## <a name="76-x509certificate2tostringbool-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>76: X509Certificate2.ToString(bool) では、.NET がときに、証明書に処理できないようになりましたはスローされません  
  
|||  
|-|-|  
|詳細|以前は、このメソッドをスロー 'true' verbose パラメーターに渡され、インストールされた証明書があった場合、.Net でサポートされていないフレームワークです。 これで、メソッドは成功し、アクセスできない、certifiate 部分を省略する有効な文字列が返されます。|  
|提案される解決策|場合によっては、API を以前スローを返される文字列が場合があります (公開キー、秘密キー、および拡張機能) などのいくつかの証明書データを除外することを期待する X509Certificate2.ToString(bool) に応じて任意のコードを更新する必要があります。|  
|スコープ|エッジ|  
|バージョン|4.6|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString%28System.Boolean%29?displayProperty=fullName>|  
|アナライザー|CD0076|  
  
<a name="diagnostic77"></a>   
## <a name="77-reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>77: アウト プロセス DCOM クライアントにマネージ コードからリフレクション オブジェクトが渡さ不要になったことができます  
  
|||  
|-|-|  
|詳細|リフレクション オブジェクトはマネージ コードからアウト プロセス DCOM クライアントに渡されなくなりました。 次の種類が影響を受けます。<br /><br /> Assembly<br /><br /> MemberInfo (および最後に、MethodInfo、種類、および間違っています。 その派生型)<br /><br /> MethodBody<br /><br /> モジュール<br /><br /> ParameterInfo。<br /><br /> 呼び出す`IMarshal`戻り値のオブジェクトの`E_NOINTERFACE`です。|  
|提案される解決策|非リフレクション オブジェクトの処理をマーシャ リング コードを更新します。|  
|スコープ|マイナー|  
|バージョン|4.6|  
|型|ランタイム|  
|アナライザー|CD0077|  
  
<a name="diagnostic78"></a>   
## <a name="78-contentdisposition-datetimes-returns-slightly-different-string"></a>78: します DateTimes が若干異なる文字列を返します。  
  
|||  
|-|-|  
|詳細|4.6 では、常に 2 桁の数字を持つ日付時刻の時間部分を表すために、ContentDispositions の文字列形式が更新されました。 これは、遵守[RFC822](http://www.ietf.org/rfc/rfc0822.txt)と[RFC2822](http://www.ietf.org/rfc/rfc2822.txt)します。 これにより、 `ContentDisposition.ToString` 10時 00分 AM 前に、の廃棄の時間要素のいずれかの場所のシナリオで 4.6 で若干異なる文字列を返します。 ContentDispositions がします。 ToString 処理、シリアル化、および GetHashCode 呼び出しを確認する必要がありますので、文字列に変換してから使用してもシリアル化されることに注意してください。|  
|提案される解決策|ContentDispositions の文字列形式をさまざまな .NET Framework のバージョンが、相互に正しくと比べてみることを期待できません。 可能であれば、比較を行う前に、ContentDispositions に文字列を変換します。|  
|スコープ|マイナー|  
|バージョン|4.6|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=fullName><br /><br /> <xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=fullName>|  
|アナライザー|CD0078|  
  
<a name="diagnostic82"></a>   
## <a name="82-workflowdesignerload-doesnt-remove-symbol-property"></a>82: WorkflowDesigner.Load はシンボル プロパティを削除しません。  
  
|||  
|-|-|  
|詳細|ワークフロー デザイナーおよび WorkflowDesigner.Load() メソッドを使用して再ホストされた 3.5 のワークフローの読み込みで .NET Framework 4.5 を対象とする場合は、ワークフローの保存中に、XamlDuplicateMemberException がスローされます。|  
|提案される解決策|このバグは、ワークフロー デザイナーでの周りを設定して動作できるように .NET Framework 4.5 を対象とする場合にのみマニフェスト、 `WorkflowDesigner.Context.Services.GetService<DesignerConfigurationService>().TargetFrameworkName` 4.0 の .NET Framework にします。<br /><br /> 使用して、問題を回避する代わりに、 [WorkflowContext.Load(string)](https://msdn.microsoft.com/en-us/library/ee425926\(v=vs.110\).aspx)メソッドの代わりに、ワークフローの読み込みを[WorkflowDesigner.Load()](https://msdn.microsoft.com/en-us/library/ee403482\(v=vs.110\).aspx)します。|  
|スコープ|Major|  
|バージョン|4.5-4.5.2|  
|型|再ターゲット中|  
|影響を受ける Api|<xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=fullName>|  
|アナライザー|CD0082|  
  
<a name="diagnostic83"></a>   
## <a name="83-sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a>83: IFS Winsock BSP または LSP があると Windows 7 で SqlConnection.Open が失敗します。  
  
|||  
|-|-|  
|詳細|SqlConneciton.Open および OpenAsync は、コンピューター上に存在する IFS Winsock BSP または LSP が Windows 7 コンピューターで実行されている場合は .NET Framework 4.5 で失敗します。<br /><br /> IFS BSP 以外または LSP がインストールされているかどうかを確認するのには、使用、`netsh WinSock Show Catalog`コマンド、および確認すべて`Winsock Catalog Provider Entry`返される項目です。 サービスのフラグ値がある場合、`0x20000`ビットが設定されて、プロバイダーが IFS のハンドルを使用して、正しく機能します。 場合、`0x20000`ビットはクリアされます (設定しません)、IFS BSP 以外または LSP をお勧めします。|  
|提案される解決策|このバグについては .NET framework 4.5.2、修正が .NET Framework をアップグレードすることによって回避できるようにします。 また、すべてインストールされている非-IFS Winsock Lsp を削除することで回避できます。|  
|スコープ|マイナー|  
|バージョン|4.5-4.5.2|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=fullName><br /><br /> <xref:System.Data.SqlClient.SqlConnection.OpenAsync%28System.Threading.CancellationToken%29?displayProperty=fullName>|  
|アナライザー|CD0083|  
  
<a name="diagnostic84"></a>   
## <a name="84-icommandcanexecutechanged-event-behaviour-changed-in-net-45"></a>84: ICommand.CanExecuteChanged イベントの動作は .NET 4.5 で変更されました。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.5 では、イベントの送信元イベントを発生させたオブジェクトと同じオブジェクトされていない限り、CanExecuteChangedEvent が無視されました。 このバグは、.NET Framework 4.5 servcing 更新プログラムで修正されました。|  
|提案される解決策|このバグは、サービスでは、.NET Framework が最新であることを確認することで、または .NET Framework 4.5.1 へのアップグレードによって回避できるようにをリリース、.NET Framework 4.5 で修正がされています。 または、ICommand を使ったアプリケーション コードを変更して、CanExecuteChanged コマンドを発生させる場合、送信者がイベントを発生させるオブジェクトと同じであるかどうかを確認できます。|  
|スコープ|マイナー|  
|バージョン|4.5-4.5|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=fullName>|  
|アナライザー|CD0084|  
  
<a name="diagnostic85"></a>   
## <a name="85-some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a>85: 初回 (処理) が発生する一部の .NET Api EntryPointNotFoundExceptions  
  
|||  
|-|-|  
|詳細|.NET Framework 4.5 では、少数の .NET メソッドは、初回 EntryPointNotFoundExceptions をスローすることが開始されました。 .Net 内でこれらの例外が処理されたフレームワーク、初回例外が予期しないテスト自動化を損なうことができます。 これらと同じ Api は、HighVersionLie が有効になっているときに、いくつかの ApiVerifier シナリオを中断します。|  
|提案される解決策|このバグは、.NET Framework 4.5.1 をアップグレードすることで回避できます。 また、テスト自動化に初回 EntryPointNotFoundExceptions で中断しない更新できます。|  
|スコープ|エッジ|  
|バージョン|4.5-4.5.1|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Diagnostics.Debug.Assert%28System.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%2CSystem.String%29?displayProperty=fullName><br /><br /> [Debug.Assert (オブジェクトのブール値、文字列、文字列、\<xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%29?displayProperty=fullName>|  
|アナライザー|CD0085|  
  
<a name="diagnostic86"></a>   
## <a name="86-scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a>86: WPF TreeView コントロールまたは、VirtualizingStackPanel でグループ化された ListBox のスクロール、ハングが発生することができます  
  
|||  
|-|-|  
|詳細|.NET Framework v4.5、仮想化されたスタック パネルで WPF TreeView をスクロールすることがありますハング (または ItemsPresenter 要素をツリー ビューなどの項目) の間、ビューポートに余白がある場合。 さらに、場合によっては、ビュー内のさまざまなサイズ設定されたアイテムことがありますが不安定になる場合でも、余白はありません。|  
|提案される解決策|このバグは、.NET Framework 4.5.1 をアップグレードすることで回避できます。 また、格納されているすべての項目が同じサイズである場合は、余白を (Treeview) のような仮想化されたスタック パネル内のビューのコレクションから削除できます。|  
|スコープ|Major|  
|バージョン|4.5-4.5.1|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing%28System.Windows.DependencyObject%2CSystem.Boolean%29?displayProperty=fullName>|  
|アナライザー|CD0086<br /><br /> CD0086|  
  
<a name="diagnostic89"></a>   
## <a name="89-typeisassignablefrom-returns-wrong-result-for-generic-variables-with-constraints"></a>89: Type.IsAssignableFrom には、制約を持つジェネリック変数の間違った結果が返されます。  
  
|||  
|-|-|  
|詳細|.NET Framework 4.5 で Type.IsAssignableFrom は正しくを返すこと`false`いくつかの制約のジェネリック型のすべてのケースにします。|  
|提案される解決策|この問題は、サービスの更新プログラムで修正されました。 この問題を解決する .NET Framework 4.5、または .NET Framework 4.5.1 へのアップグレード、またはそれ以降に更新してください。 またをジェネリック パラメーターの制約を持つジェネリック型で IsAssignableFrom を使用しないでください。 解決策としては、リフレクション Api を使用できます。|  
|スコープ|マイナー|  
|バージョン|4.5-4.5|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Type.IsAssignableFrom%28System.Type%29?displayProperty=fullName>|  
|アナライザー|CD0089<br /><br /> CD0089|  
  
<a name="diagnostic91"></a>   
## <a name="91-entityframework-60-loads-very-slowly-in-apps-launched-from-visual-studio"></a>91: entity Framework 6.0 は、Visual Studio から起動されたアプリケーションで非常に遅いが読み込まれる  
  
|||  
|-|-|  
|詳細|Entity Framework 6.0 を使用する Visual Studio 2013 からアプリを起動すると、非常に遅いことができます。|  
|提案される解決策|EntityFramework 6.0.2 では、この問題が解決します。 パフォーマンスの問題を回避する entity Framework を更新してください。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|アナライザー|CD0091|  
  
<a name="diagnostic92"></a>   
## <a name="92-multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a>92: AntiXSSEncoder を使用する場合、ASP.Net の TextBox を複数行の間隔が変更されました  
  
|||  
|-|-|  
|詳細|.NET Framework 4.0 で行を追加する間に挿入された行のポストバックでは、上の複数行テキスト ボックスを使用する場合、`AntiXSSEncoder`です。 .NET Framework 4.5 でこれらの余分な改行は、web アプリが .NET 4.5 を対象とする場合にのみ|  
|提案される解決策|複数行テキスト ボックスが不要になった余分な改行を挿入するように改良を 4.0 の web アプリが .NET 4.5 に再ターゲットであることに注意してください。 これが望ましくない場合、アプリケーションで、.NET Framework 4.0 を対象とする .NET Framework 4.5 で実行されているときに以前の動作ができます。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|再ターゲット中|  
|アナライザー|CD0092|  
  
<a name="diagnostic95"></a>   
## <a name="95-concurrentqueuettrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>95: ConcurrentQueue<>\>します。TryPeek は、その出力パラメーターを使用してエラーがある null を返すことができます。  
  
|||  
|-|-|  
|詳細|一部のマルチ スレッドのシナリオで`ConcurentQueue<T>.TryPeek`true を返すことができますが、(適切なピーク値) ではなく null 値を持つ出力パラメーターを設定します。|  
|提案される解決策|.NET Framework 4.5.1 では、この問題が解決します。 そのフレームワークにアップグレードすると、問題が解決されます。|  
|スコープ|Major|  
|バージョン|4.5-4.5.1|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek%28%600%40%29?displayProperty=fullName>|  
|アナライザー|CD0095|  
  
<a name="diagnostic98"></a>   
## <a name="98-multiple-items-in-a-single-tablelayoutpanel-cell-may-be-rearranged"></a>98: 単一 TableLayoutPanel セル内の複数の項目を並べ替えることができます  
  
|||  
|-|-|  
|詳細|.NET Framework 4.5 で同じの TableLayoutPanel セル内に複数の項目が配置されている場合可能性がありますで表示されるよう、別の順序よりも、.NET Framework 4.0 にします。|  
|提案される解決策|この動作は、.NET Framework 4.5 をサービスの更新プログラムに復元されました。 この問題を解決する .NET Framework 4.5、または .NET Framework 4.5.1 へのアップグレード、またはそれ以降に更新してください。 また、同じ TableLayourPanel セル内の複数の項目のあいまいなケースを回避します。|  
|スコープ|マイナー|  
|バージョン|4.5-4.5|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Windows.Forms.TableLayoutControlCollection.Add%28System.Windows.Forms.Control%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>|  
|アナライザー|CD0098|  
  
<a name="diagnostic100"></a>   
## <a name="100-foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a>100: Foreach 反復子変数の現在のスコープ、イテレーションに含まれるため、クロージャのキャプチャのセマンティクスは、(C&5;) で異なります  
  
|||  
|-|-|  
|詳細|C# 5 (Visual Studio 2012) 以降では、foreach 反復子変数は、イテレーションごとにスコープされます。 Foreach のクロージャに含まれないように、変数に依存したコードしていた場合は、区切りができます。 という症状は、この変更は、代表に渡された反復子変数が、デリゲートが呼び出された時点の値ではなく、デリゲートの作成時の値として処理することになります。|  
|提案される解決策|理想的には、新しいコンパイラの動作を期待するコードを更新する必要があります。 古いセマンティクスが必要な場合は、ループのスコープ外で明示的に配置されている別々 の変数を反復子変数を交換できます。|  
|スコープ|Major|  
|バージョン|4.5|  
|型|再ターゲット中|  
|アナライザー|CD0100|  
  
<a name="diagnostic101"></a>   
## <a name="101-htmltextwriter-does-not-render-br-element-correctly"></a>101: HtmlTextWriter が表示されません。\`<br>\>' 要素正しく  
  
|||  
|-|-|  
|詳細|呼び出す .NET Framework 4.6 では、以降で`HtmlTextWriter.RenderBeginTag()`と`HtmlTextWriter.RenderEndTag()`で、`<BR />`要素が 1 つだけに挿入することが正しく`<BR />`ではなく 2 つ)|  
|提案される解決策|アプリは、余分なに依存している場合`<BR />`タグ、`HtmlTextWriter.RenderBeginTag()`をもう一度呼び出す必要があります。 この動作を変更するには、ので、別のオプションは従来の動作を取得するために、.NET Framework の以前のバージョンを対象とする .NET Framework 4.6 では、対象とするアプリにのみ影響します。|  
|スコープ|エッジ|  
|バージョン|4.6|  
|型|再ターゲット中|  
|影響を受ける Api|<xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.Web.UI.HtmlTextWriterTag%29?displayProperty=fullName>|  
|アナライザー|CD0101|  
  
<a name="diagnostic104"></a>   
## <a name="104-calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>104: WPF ListBox、ListView、または選択された項目がある DataGrid での通話 Items.Refresh 要素に表示される項目の重複が発生することができます  
  
|||  
|-|-|  
|詳細|.NET Framework 4.5 では、リスト ボックス内の項目が選択されている間は、コードから ListBox.Items.Refresh を呼び出すと、選択した項目を一覧内で重複するが発生することができます。 ListView コントロールと DataGrid と同様の問題が発生します。 これは、.NET Framework 4.6 で修正されます。|  
|提案される解決策|プログラムで選択を解除する項目の更新が呼び出される前に再を選択し、それらの呼び出しが完了した後でこの問題を回避することがあります。 または、この問題は、.NET Framework 4.6 で修正されています、.NET Framework のバージョンにアップグレードすることでアドレス指定すること。|  
|スコープ|マイナー|  
|バージョン|4.5-4.6|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Windows.Data.CollectionView.Refresh?displayProperty=fullName>|  
|アナライザー|CD0104|  
  
<a name="diagnostic105"></a>   
## <a name="105-etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>105: ETW EventListeners (TPL プロバイダー) のような明示的なキーワードとプロバイダーからのイベントがキャプチャされていません。  
  
|||  
|-|-|  
|詳細|キーワードの空のマスクを持つ ETW EventListeners は、正しく明示的なキーワードとプロバイダーからのイベントをキャプチャしません。 .NET Framework 4.5 では、TPL プロバイダーは、明示的なキーワードを提供することに開始され、この問題が発生します。 .NET Framework 4.6 では、EventListeners が不要になったこの問題があると更新されました。|  
|提案される解決策|この問題を回避するには、明示的に使用する「キーワード」マスクを指定するオーバー ロードを EnableEvents への呼び出しに EnableEvents (eventSource、レベル) の呼び出しを置き換える:`EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))`です。<br /><br /> または、この問題は、.NET Framework 4.6 で修正されています、.NET Framework のバージョンにアップグレードすることでアドレス指定すること。|  
|スコープ|エッジ|  
|バージョン|4.5-4.6|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%29?displayProperty=fullName>|  
|アナライザー|CD0105|  
  
<a name="diagnostic109"></a>   
## <a name="109-building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>109: Visual Studio 2013 で、Entity Framework edmx を構築できる場合エラーで失敗 MSB4062 EntityDeploySplit または EntityClean タスクを使用します。  
  
|||  
|-|-|  
|詳細|MSBuild 12.0 ツール (Visual Studio 2013 に含まれる) には、古い Entity Framework のターゲット ファイルが無効になる原因と、msbuild ファイルの場所が変更されました。 その結果`EntityDeploySplit`と`EntityClean`を見つけることはないために、タスクが失敗する`Microsoft.Data.Entity.Build.Tasks.dll`です。 この区切りは、ツールセット (msbuild/VS) 変更されるため、.NET Framework の変更のために注意してください。 単なる .NET Framework をアップグレードするときではなく、開発者ツールをアップグレードするときにのみ実行されます。|  
|提案される解決策|Entity Framework のターゲット ファイルは、msbuild レイアウト以降の新機能には、.NET Framework 4.6 を使用する固定です。 Framework のバージョンにアップグレードすると、この問題を解決します。 または、[この](http://stackoverflow.com/a/24249247/131944)回避策は、ターゲット ファイルを直接修正プログラムを使用できます。|  
|スコープ|Major|  
|バージョン|4.5.1-4.6|  
|型|再ターゲット中|  
|アナライザー|CD0109|  
  
<a name="diagnostic111"></a>   
## <a name="111-xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a>111: 現在、XSD スキーマの検証は、複合キーを使用して、1 つのキーが空の場合正しく unique 制約の違反を検出  
  
|||  
|-|-|  
|詳細|4.6 の前に .NET Framework のバージョンでは、キーのいずれかが空の場合、複合キーの一意性制約を検出しないように XSD 検証を原因となったバグがありました。 .NET Framework 4.6 では、この問題を修正しました。 適切な検証は、この結果が、以前を持つで検証されないいくつかの XML にする可能性もあります。|  
|提案される解決策|.NET Framework 4.0 の検証が必要、緩やかな場合は、検証中のアプリケーションがバージョン 4.5 (またはそれ以前) をターゲット .NET Framework のです。 .NET 4.6 に再ターゲットとただし、コード レビューは、重複の複合キーでの説明に従ってこの問題の説明) が予期されていないを検証するかどうかを必ず行ってください。|  
|スコープ|エッジ|  
|バージョン|4.6|  
|型|再ターゲット中|  
|アナライザー|CD0111|  
  
<a name="diagnostic112"></a>   
## <a name="112-calling-attributegetcustomattributes-on-an-indexer-property-no-longer-throws-ambiguousmatchexception-if-the-ambiguity-can-be-resolved-by-indexs-type"></a>112: 通話 Attribute.GetCustomAttributes インデクサー プロパティには、インデックスの種類によって、あいまいさを解決できる場合は、不要になった AmbiguousMatchException をスロー  
  
|||  
|-|-|  
|詳細|.NET Framework 4.6 を呼び出す前に`GetCustomAttribute(s)`インデクサー上で、インデックスの種類によってのみ別のプロパティからと一致しません。 プロパティになる、`AmbiguousMatchException`です。 以降、.NET Framework 4.6 では、プロパティの属性が正しく返されます。|  
|提案される解決策|GetCustomAttribute(s) が動作するより頻繁にここで注意してください。 アプリケーションに依存していた場合、 `AmbiguousMatchException`、明示的に複数のインデクサーの代わりに検索するにリフレクションを使用する必要があります。|  
|スコープ|エッジ|  
|バージョン|4.6|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Attribute.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%60%601%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%60%601%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%60%601%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%60%601%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName>|  
|アナライザー|CD0112|  
  
<a name="diagnostic113"></a>   
## <a name="113-intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a>113: ItemsControls (リスト ボックスや DataGrid) などの下位の項目にスクロールすることができません断続的にカスタム Datatemplate を使用する場合  
  
|||  
|-|-|  
|詳細|場合によっては、.NET Framework 4.5 でのバグを引き起こしている ItemsControls (リスト ボックス、コンボ ボックス、DataGrid など) など、下位の項目にスクロールしないにカスタム Datatemplate を使用するとします。 スクロールが行われると (スクロールすると、バックアップを作成) 後にもう一度動作かどうかは、です。|  
|提案される解決策|この問題は、.NET framework 4.5.2 は修正され、.NET Framework のバージョン (またはそれ以降のバージョン) にアップグレードすることでアドレス指定することです。 また、ユーザーは、これらのコレクションの最後のアイテムにスクロール バーをドラッグできますが、正常に操作を&2; 回行おうとする必要があります。|  
|スコープ|マイナー|  
|バージョン|4.5-4.5.2|  
|型|ランタイム|  
|アナライザー|CD0113|  
  
<a name="diagnostic114"></a>   
## <a name="114-glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-45"></a>114: GlyphRun.ComputeInkBoundingBox() と FormattedText.Extent .NET 4.5 以降で別の値を返す  
  
|||  
|-|-|  
|詳細|ボックスが小さすぎるため、場合によっては、.NET Framework 4.0 に含まれるグリフの GlyphRun.ComputeInkBoundingBox() と問題に対応する .NET Framework 4.5 で FormattedText.Extent に改善が加えられました。 その結果は、UI レイアウトにわずかな違いに .NET Framework 4.5 での大規模な先頭がいくつかの境界ボックスになります。|  
|提案される解決策|いくつかのグリフの境界ボックス サイズが増加したことに注意してください。 これらの変更は、通常、向上プレゼンテーション ヒット ボックス、およびテストが、古い (事前 .NET 4.5) の動作を使用する場合は、そのことができます 10 営業日に app.config ファイルに次のエントリを追加することで。<br /><br /> `<appsettings> <add key="IncludeAllInkInBoundingBox" value="false"> </appsettings>`|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=fullName><br /><br /> <xref:System.Windows.Media.FormattedText.Extent?displayProperty=fullName>|  
|アナライザー|CD0114|  
  
<a name="diagnostic124"></a>   
## <a name="124-calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>124: CellEditEnding ハンドラーから呼び出す DataGrid.CommitEdit フォーカスを削除します。  
  
|||  
|-|-|  
|詳細|DataGrid の CellEditEnding イベント ハンドラーのいずれかから DataGrid.CommitEdit を呼び出すと、フォーカスが失われ、DataGrid とします。|  
|提案される解決策|このバグについては .NET framework 4.5.2、修正が .NET Framework をアップグレードすることによって回避できるようにします。 また、明示的に再 CommitEdit を呼び出した後、データ グリッドを選択して回避できます。|  
|スコープ|エッジ|  
|バージョン|4.5-4.5.2|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName><br /><br /> <xref:System.Windows.Controls.DataGrid.CommitEdit%28System.Windows.Controls.DataGridEditingUnit%2CSystem.Boolean%29?displayProperty=fullName>|  
|アナライザー|CD0124|  
  
<a name="diagnostic125"></a>   
## <a name="125-aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>125: ASP.NET MVC はルート パラメーターに渡された文字列に含まれるスペースをエスケープするようになりました  
  
|||  
|-|-|  
|詳細|RFC 2396 に準拠させるためにルートからのアクション パラメーターを設定するときに、ルートのパスにスペースはエスケープようになりました。 そのため、一方`/controller/action/some data`ルートと一致した`/controller/action/{data}`でき、`some data`データ パラメーターとしてその機能が追加されました`some%20data`代わりにします。|  
|提案される解決策|コードを更新すると、ルートから文字列パラメーターをエスケープ解除する必要があります。 元の URI が必要な場合は、Request.RequestUri.OriginalString API にアクセスできます。|  
|スコープ|マイナー|  
|バージョン|4.5.2|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Web.Http.RouteAttribute.%23ctor%28System.String%29?displayProperty=fullName>|  
|アナライザー|CD0125|  
  
<a name="diagnostic127"></a>   
## <a name="127-vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>127: VB.NET では System.Windows Api の部分的な名前空間の修飾がサポートしていません  
  
|||  
|-|-|  
|詳細|.NET 4.5.2 の以降では、VB.NET プロジェクトは部分修飾名前空間を持つ System.Windows Api を指定できません。 たとえばを参照する`Windows.Forms.DialogResult`は失敗します。 代わりに、コードは、完全修飾名を参照する必要があります (`System.Windows.Forms.DialogResult`) または特定の名前空間をインポートし、だけを参照してください`DialogResult`します。|  
|提案される解決策|参照するコードを更新する必要があります`System.Windows`Api 単純な名前 (および関連する名前空間をインポートする)、または完全修飾名。|  
|スコープ|マイナー|  
|バージョン|4.5.2|  
|型|再ターゲット中|  
|アナライザー|CD0127|  
  
<a name="diagnostic129"></a>   
## <a name="129-two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a>129: 非パブリック setter を使用してプロパティに双方向データ バインドはサポートされていません  
  
|||  
|-|-|  
|詳細|しようとせず、パブリックな setter プロパティへのデータ バインドがかつてないシナリオをサポートします。 .NET framework 4.5.1 以降では、このシナリオでは、InvalidOperationException がスローされます。 具体的には、.NET Framework 4.5.1 を対象とするアプリに対して新しい例外がスローだけに注意してください。 アプリが .NET Framework 4.5 をターゲットの呼び出しが許可されます。 アプリケーションは、特定の .NET Framework バージョンを対象としない場合、バインドが扱われます一方向として。|  
|提案される解決策|一方向のバインドを使用するか、プロパティの set アクセス操作子を公開する、アプリケーションを更新する必要があります。 また、.NET Framework 4.5 を対象とするにより、アプリ以前の動作が発生することです。|  
|スコープ|マイナー|  
|バージョン|4.5.1|  
|型|再ターゲット中|  
|影響を受ける Api|<xref:System.Windows.Data.BindingMode?displayProperty=fullName>|  
|アナライザー|CD0129|  
  
<a name="diagnostic130"></a>   
## <a name="130-marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>130: Marshal.SizeOf と Marshal.PtrToStructure オーバー ロード中断動的なコード  
  
|||  
|-|-|  
|詳細|メソッドに動的に結びつける方法、.NET Framework 4.5.1 以降で`Marshal.SizeOf`または`Marshal.PtrToStructure`(またはを使用して Windows PowerShell、IronPython、たとえば C# で dynamic キーワード、) につながる`MethodInvocationExceptions`スクリプト エンジンをあいまいにする可能性があるこれらのメソッドの新しいオーバー ロードが追加されているためです。|  
|提案される解決策|スクリプトを更新するために使用するオーバー ロードが明確に表示します。 これは普通とメソッドの型パラメーターを明示的にキャストして`System.Type`します。 参照してください[このリンク](https://support.microsoft.com/en-us/kb/2909958/)詳細と問題を解決する方法の例です。|  
|スコープ|マイナー|  
|バージョン|4.5.1|  
|型|ランタイム|  
|アナライザー|CD0130|  
  
<a name="diagnostic131"></a>   
## <a name="131-previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a>131: PreviewLostKeyboardFocus はそのハンドラーには、Windows フォーム メッセージ ボックスが表示される場合繰り返し呼び出されます。  
  
|||  
|-|-|  
|詳細|呼び出す .NET Framework 4.5 以降で`System.Windows.Forms.MessageBox.Show`から、`UIElement.PreviewLostKeyboardFocus`ハンドラーと、ハンドラーが再発生する場合、メッセージ ボックスが閉じられると、メッセージ ボックスの無限ループが可能性があります。|  
|提案される解決策|この問題に回避するために&2; つのオプションがあります。<br /><br /> 呼び出すことによって回避できます`System.Windows.MessageBox.Show`の代わりに`System.Windows.Forms.MessageBox.Show`します。<br /><br /> メッセージ ボックスを表示することによって回避できる場合があります、`LostKeyboardFocus`イベント ハンドラー (代わりに、`PreviewLostKeyboardFocus`イベント ハンドラー)。|  
|スコープ|エッジ|  
|バージョン|4.5|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=fullName><br /><br /> <xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=fullName><br /><br /> <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName><br /><br /> <xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=fullName>|  
|アナライザー|CD0131|  
  
<a name="diagnostic133"></a>   
## <a name="133-a-concurrentdictionary-serialized-in-net-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-451-or-452"></a>133: NetDataContractSerializer で .NET 4.5 でシリアル化された ConcurrentDictionary は .NET 4.5.1 または 4.5.2 で逆シリアル化することはできません  
  
|||  
|-|-|  
|詳細|型、内部の変更により`System.Collections.Concurrent.ConcurrentDictionary`.NET Framework 4.5 にシリアル化されるオブジェクトを使用して、 `NetDataContractSerializer` .NET framework 4.5.2 または .NET Framework 4.5.1 で逆シリアル化することはできません。<br /><br /> 逆方向の移動に注意してください (.NET Framework でのシリアル化 4.5.x と .NET Framework 4.5 に逆シリアル化) は機能します。 同様に、すべての 4.x バージョン間のシリアル化は、.NET Framework 4.6 で動作します。<br /><br /> シリアル化して、1 つのバージョンの .NET Framework で逆シリアル化は影響はありません。|  
|提案される解決策|.NET Framework 4.5 と .NET Framework 4.5.1/4.5.2 間 ConcurrentDictionary を逆シリアル化およびシリアル化する必要がある場合は、NetDataContractSerializer ではなく、DataContractSerializer または BinaryFormatter シリアライザーなどの代替のシリアライザーを使用してください。<br /><br /> または、.NET Framework 4.6 は、この問題を説明、.NET Framework のバージョンにアップグレードすることで解決可能性があります。|  
|スコープ|マイナー|  
|バージョン|4.5.1-4.6|  
|型|ランタイム|  
|アナライザー|CD0133|  
  
<a name="diagnostic134"></a>   
## <a name="134-persian-calendar-now-uses-the-hijri-solar-algorithm"></a>134: ペルシャ暦では、イスラム暦の太陽アルゴリズムを使用  
  
|||  
|-|-|  
|詳細|以降、.NET Framework 4.6 では、PersianCalendar クラスは、イスラム暦の太陽アルゴリズムを使用します。 PersianCalendar と他のカレンダーの日付に変換すると、1800 より前または 2023 (グレゴリオ暦) よりも後の日付の .NET Framework 4.6 をわずかに異なる結果の先頭が生じる場合があります。<br /><br /> また、`PersianCalendar.MinSupportedDateTime`現在`March 22, 0622 instead of March 21, 0622`します。|  
|提案される解決策|.NET 4.6 で、PersianCalendar を使用する場合の早期または遅延の日付が若干異なる場合があります注意してください。 また、異なる .NET Framework のバージョンを実行することがプロセス間で日付をシリアル化するときは保存 PersianCalendar 日付文字列として (ため、これらの値が異なる場合があります)。|  
|スコープ|マイナー|  
|バージョン|4.6|  
|型|ランタイム|  
|影響を受ける Api|<xref:System.Globalization.PersianCalendar?displayProperty=fullName>|  
|アナライザー|CD0134|  
  
<a name="diagnostic138"></a>   
## <a name="138-calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>138: null 引数による呼び出し CreateDefaultAuthorizationContext が変更されました。  
  
|||  
|-|-|  
|詳細|呼び出しによって返される、AuthorizationContext の実装、`CreateDefaultAuthorizationContext(IList<IAuthorizationPolicy>)`引数には null authorizationPolicies と .NET Framework 4.6 では、その実装が変更されました。|  
|提案される解決策|まれに、カスタム認証を使用する WCF アプリの動作に違いが生じる可能性があります。 このような場合は、2 つの方法のいずれかで、以前の動作を復元できます。<br /><br /> 4.6 よりも前のバージョンの .NET Framework を対象とするようにアプリを再コンパイルする。 IIS でホストされるサービスを使用して、 <httpRuntime targetframework="x.x"></httpRuntime> \>以前のバージョンの .NET Framework を対象とする要素。<br /><br /> 次の行を追加、 `<appSettings>` app.config ファイルのセクション。`<add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />`|  
|スコープ|マイナー|  
|バージョン|4.6|  
|型|再ターゲット中|  
|影響を受ける Api|<xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%28System.Collections.Generic.IList%7BSystem.IdentityModel.Policy.IAuthorizationPolicy%7D%29?displayProperty=fullName>|  
|アナライザー|CD0138|  
  
<a name="diagnostic141"></a>   
## <a name="141-wpf-treeviewitem-must-be-used-within-a-treeview"></a>141: WPF TreeViewItem をツリー ビュー内で使用する必要があります  
  
|||  
|-|-|  
|詳細|変更は、外部 TreeView で TreeViewItem 要素の使用量を制限する 4.5 で導入されました。 次の条件下で明らかにします。<br /><br /> TreeViewItem のビジュアルの親は、パネルではありません。 (ツリー ビューの生成 TreeViewItem を含むパネル親として)<br /><br /> リスト コントロール (ListBox、DataGrid、ListView など) の「アイテム ホスト」として機能する VirtualizingStackPanel の子孫である、TreeViewItem です。 仮想化を有効にする必要はありません。<br /><br /> 項目のスクロール、VirtualizingStackPanel は、(`ScrollUnit="Item"`)。<br /><br /> 呼び出されると`VirtualizingStackPanel.MakeVisible(v)`要素をスクロールする`v`表示にします。 これは、ため、明示的または暗黙的にでは、さまざまな方法です。おそらく、最も一般的な方法をクリックするだけで`v`にキーボード フォーカスを設定します。<br /><br /> ビジュアルの親チェーンから`v`TreeViewItem を VirtualizingStackPanel 通過します。<br /><br /> つまり、これは、TreeView の外部で TreeViewItem を使用しに表示を TreeViewItem の子孫である、ユーザーがクリックしたときに発生します。 フォーカスを取得できる子孫、TreeViewItem がない場合は、この問題を決して表示されます。 これは、ヒット、状況の例は、TreeViewItem DataTemplate のルートです。  この問題にヒットした場合は、WPF フレームワーク内で行われる InvalidCastException があります。|  
|提案される解決策|修正プログラムが利用できるこの。|  
|スコープ|マイナー|  
|バージョン|4.5|  
|型|ランタイム|  
|アナライザー|CD0141|  
  
<a name="diagnostic143"></a>   
## <a name="143-x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>143: X509CertificateClaimSet.FindClaims すべて claimTypes を考慮します。  
  
|||  
|-|-|  
|詳細|アプリで .NET Framework 4.6.1、対象とする場合は、SAN フィールド内の複数の DNS エントリを含む証明書から身元証明データ セットが初期化される、X509 FindClaims メソッドしようと claimType 引数のすべての DNS エントリと一致します。<br /><br /> 以前のバージョンの .NET Framework を対象とするアプリの場合は、FindClaims メソッドは、最後の DNS エントリとのみ claimType 引数との照合を試みます。|  
|提案される解決策|この変更には、.NET Framework 4.6.1 を対象とするアプリケーションのみに影響します。 この変更できないことがあります (場合に有効または対象とする事前&4;.6.1) で、 [DisableMultipleDNSEntries](https://msdn.microsoft.com/en-us/library/mt620030%28v=vs.110%29.aspx)互換性スイッチ。|  
|スコープ|マイナー|  
|バージョン|4.6.1|  
|型|再ターゲット中|  
|影響を受ける Api|<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%28System.String%2CSystem.String%29?displayProperty=fullName>|  
|アナライザー|CD0143|  
  
<a name="diagnostic144"></a>   
## <a name="144-applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>144: Application.FilterMessage が不要になった IMessageFilter.PreFilterMessage の再入可能な実装についてをスロー  
  
|||  
|-|-|  
|詳細|以前の .NET Framework 4.6.1、(Application.DoEvents を呼び出しても) 中、IMessageFilter.PreFilterMessage と Application.FilterMessage どのと呼ばれる AddMessageFilter または RemoveMessageFilter を呼び出すと、IndexOutOfRangeException が発生すると。<br /><br /> 以降、.NET Framework 4.6.1 を対象とするアプリケーションでは、この例外がスローされなく、および再入可能なフィルター上で述べたを使用できます。|  
|提案される解決策|上記で説明した、再入可能な IMessageFilter.PreFilterMessage 動作のために Application.FilterMessage をスローしないことに注意してください。 これには、.NET Framework 4.6.1 を対象とするアプリケーションのみに影響します。<br /><br /> .NET Framework 4.6.1 を対象とするアプリを解除できますこの変更 (またはアプリのターゲットの古いフレームワークにオプトイン可能性があります) を使用して、 [DontSupportReentrantFilterMessage](https://msdn.microsoft.com/en-us/library/mt620032%28v=vs.110%29.aspx)互換性スイッチ。|  
|スコープ|エッジ|  
|バージョン|4.6.1|  
|型|再ターゲット中|  
|影響を受ける Api|<xref:System.Windows.Forms.Application.FilterMessage%28System.Windows.Forms.Message%40%29?displayProperty=fullName>|  
|アナライザー|CD0144|  
  
<a name="diagnostic145"></a>   
## <a name="145-currentculture-is-not-preserved-across-wpf-dispatcher-operations"></a>145: WPF ディスパッチャー操作 CurrentCulture は維持されません  
  
|||  
|-|-|  
|詳細|以降、.NET Framework 4.6 では、内で行われたか、CurrentCulture、CurrentUICulture への変更、[ディスパッチャー](https://msdn.microsoft.com/en-us/library/system.windows.threading.dispatcher%28v=vs.110%29.aspx)はそのディスパッチャー操作の最後に失われます。 同様に、CurrentCulture または CurrentUICulture ディスパッチャー操作外で行われた変更が反映されないことと操作が実行されます。<br /><br /> 実際には、つまり、CurrentCulture と CurrentUICulture の変更が、WPF の UI のコールバックと WPF アプリケーションでは、その他のコードの間でフロー可能性があります。<br /><br /> これは変更されるため、 [ExecutionContext](https://msdn.microsoft.com/en-us/library/system.threading.executioncontext%28v=vs.110%29.aspx) CurrentCulture と CurrentUICulture は、.NET Framework 4.6 を対象とするアプリで始まる実行コンテキストに格納される原因となった。 WPF ディスパッチャー操作では、操作を開始し、操作が完了したときに、以前のコンテキストを復元するために使用する実行コンテキストを格納します。 CurrentCulture と CurrentUICulture がそのコンテキストの一部に今すぐためディスパッチャー操作内でそれに対する変更は、操作の外部で保持されません。|  
|提案される解決策|アプリがこの変更によって影響を受ける可能性があることによって回避目的 CurrentCulture を格納するまたは currentuiculture の各フィールドにしてすべてのディスパッチャー操作で確認する、正しい CurrentCulture と CurrentUICulture が設定されている (UI イベントのコールバック ハンドラー) を含む本文。 します。 または、ExecutionContext を変更する基になるため、この WPF 変更では、.NET Framework 4.6 以降を対象とするアプリのみに影響、.NET Framework 4.5.2 を対象とするでは、この中断を回避できます。|  
|スコープ|マイナー|  
|バージョン|4.6|  
|型|再ターゲット中|  
|アナライザー|CD0145|