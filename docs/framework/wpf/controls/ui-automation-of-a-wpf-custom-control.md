---
title: "WPF カスタム コントロールの UI オートメーション | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "UI オートメーションを適用するカスタム コントロール [WPF]"
  - "カスタム コントロールに適用することにユーザー補助 [WPF]"
  - "ユーザー補助機能を向上させるカスタム コントロール [WPF]"
  - "カスタム コントロールで使用する UI オートメーション [WPF]"
ms.assetid: 47b310fc-fbd5-4ce2-a606-22d04c6d4911
caps.latest.revision: 34
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 34
---
# WPF カスタム コントロールの UI オートメーション
[!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)]クライアントを確認またはさまざまなプラットフォームやフレームワークのユーザー インターフェイスの操作を使用してその自動化機能を単一の汎用的なインターフェイスを提供します。 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]品質保証 (テスト) のコードとユーザー インターフェイス要素を調べて、他のコードからそれらにユーザーの操作をシュミレーションにスクリーン リーダーなどのユーザー補助アプリケーションの両方を使用できます。 については[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]すべてのプラットフォームでは、ユーザー補助機能を参照してください。  
  
 このトピックでは、WPF アプリケーションで実行されるカスタム コントロール用のサーバー側 UI オートメーション プロバイダーを実装する方法について説明します。 WPF でサポートされる[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]ピア オートメーション オブジェクトのツリーで、ユーザー インターフェイス要素のツリーに似ています。 コードとユーザー補助機能がピア オブジェクトを使用して直接 (インプロセス コード用) を提供するアプリケーションをテストまたは汎用化されたインターフェイスによって提供される[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]します。  
  
 
  
<a name="AutomationPeerClasses"></a>   
## <a name="automation-peer-classes"></a>オートメーション ピア クラス  
 コントロールがサポートする WPF[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]ピア クラスから派生するツリーを通じた<xref:System.Windows.Automation.Peers.AutomationPeer>します。 規則は、ピア クラス名は、コントロールのクラス名で始まるし、"AutomationPeer"で終了します。 たとえば、 <xref:System.Windows.Automation.Peers.ButtonAutomationPeer>のピア クラスである、<xref:System.Windows.Controls.Button>コントロール クラス。 ピア クラスはほぼ同じ[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]コントロール型が、合わせて[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]要素。 オートメーション コード経由での WPF アプリケーションにアクセスする、[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]インターフェイスがオートメーション ピアを直接使用されませんが、同じプロセス空間での自動化のサンプル コードでは、オートメーション ピアを直接使用することができます。  
  
<a name="BuiltInAutomationPeerClasses"></a>   
## <a name="built-in-automation-peer-classes"></a>組み込みのオートメーション ピア クラス  
 要素は、スクリーン リーダー アプリケーションのユーザーによって必要な情報が含まれている場合や、ユーザー インターフェイスのアクティビティを受け入れる場合、オートメーション ピア クラスを実装します。 すべての WPF のビジュアル要素は、オートメーションのピアを持っています。 オートメーション ピアを実装するクラスの例としては、<xref:System.Windows.Controls.Button>、 <xref:System.Windows.Controls.TextBox>と<xref:System.Windows.Controls.Label>します。 オートメーション ピアを実装していないクラスの例から派生するクラスには<xref:System.Windows.Controls.Decorator>など<xref:System.Windows.Controls.Border>とクラスに基づいて<xref:System.Windows.Controls.Panel>など<xref:System.Windows.Controls.Grid>と<xref:System.Windows.Controls.Canvas>します。  
  
 基本<xref:System.Windows.Controls.Control>クラスには、対応するピア クラスがありません。 ピア クラスから派生するカスタム コントロールに対応する必要がある場合<xref:System.Windows.Controls.Control>からカスタム ピア クラスを派生する必要があります<xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>します。  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations-for-derived-peers"></a>派生ピアのセキュリティの考慮事項  
 オートメーション ピアは、部分的に信頼された環境で実行する必要があります。 UIAutomationClient アセンブリ内のコードが部分的に信頼された環境で実行が構成されていないと、オートメーション ピアのコードは、そのアセンブリを参照しないでください。 代わりに、UIAutomationTypes アセンブリのクラスを使用する必要があります。 たとえば、使用する必要があります、 <xref:System.Windows.Automation.AutomationElementIdentifiers>クラスに対応する UIAutomationTypes アセンブリから、 <xref:System.Windows.Automation.AutomationElement> UIAutomationClient アセンブリ内のクラスです。 オートメーション ピアのコードで UIAutomationTypes アセンブリを参照すると安全です。  
  
<a name="PeerNavigation"></a>   
## <a name="peer-navigation"></a>ピアのナビゲーション  
 オートメーション ピアを特定すると、プロセス内のコードを呼び出して、オブジェクトのピア ツリーを移動できます<xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A>と<xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A>メソッドです。 間のナビゲーション[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]のピアの実装によって、コントロール内の要素がサポートされている、 <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A>メソッドです。 UI オートメーション システムは、コントロール内に含まれるサブ要素のツリーを構築するには、このメソッドを呼び出しますたとえば、リスト ボックス内の項目を一覧表示します。 既定値<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=fullName>メソッドは、オートメーション ピアのツリーを構築する要素のビジュアル ツリーを走査します。 カスタム コントロールは、子要素を返す情報を伝達するか、ユーザーによる操作が許可される要素のオートメーション ピア オートメーション クライアントに公開するには、このメソッドをオーバーライドします。  
  
<a name="Customizations"></a>   
## <a name="customizations-in-a-derived-peer"></a>派生のピアでのカスタマイズ  
 すべてのクラスから派生した<xref:System.Windows.UIElement>と<xref:System.Windows.ContentElement>プロテクト仮想メソッドが含まれて<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>します。 WPF 呼び出し<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>各コントロールのオートメーションのピア オブジェクトを取得します。 コントロールの特性と機能に関する情報を取得し、対話型の使用をシミュレートするために、自動化のサンプル コードは、ピアを使用できます。 オートメーションをサポートするカスタム コントロールをオーバーライドする必要があります<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>から派生したクラスのインスタンスを返すと<xref:System.Windows.Automation.Peers.AutomationPeer>します。 たとえば、カスタム コントロールから派生している場合、 <xref:System.Windows.Controls.Primitives.ButtonBase>クラス、オブジェクトによって返される<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>から派生する必要があります<xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>します。  
  
 カスタム コントロールを実装する場合は、カスタム コントロールに固有の動作を説明する基本オートメーション ピア クラスからの"Core"メソッドをオーバーライドする必要があります。  
  
### <a name="override-oncreateautomationpeer"></a>OnCreateAutomationPeer をオーバーライドします。  
 オーバーライド、 <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>メソッドを返す、プロバイダー オブジェクトから直接または間接的に派生する必要がありますので、カスタム コントロールの<xref:System.Windows.Automation.Peers.AutomationPeer>します。  
  
### <a name="override-getpattern"></a>GetPattern をオーバーライドします。  
 オートメーション ピアは、サーバー側の実装の一部を簡略化[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]パターン インターフェイスは、プロバイダーがカスタム コントロールのオートメーションのピアで処理も必要があります。 WPF 以外のプロバイダーのようにピア コントロール パターンのサポートでのインターフェイスの実装を提供することにより、 <xref:System.Windows.Automation.Provider?displayProperty=fullName>名前空間など<xref:System.Windows.Automation.Provider.IInvokeProvider>します。 ピア自体または別のオブジェクトによっては、コントロール パターンのインターフェイスを実装することができます。 ピアの<xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A>指定したパターンをサポートするオブジェクトを返します。 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]コードの呼び出し、 <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A>メソッドを指定し、 <xref:System.Windows.Automation.Peers.PatternInterface>列挙値。 オーバーライド<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A>指定したパターンを実装するオブジェクトを返す必要があります。 コントロールが、パターンのカスタム実装を持たない場合の基本型の実装を呼び出すことができます<xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A>をこの種類のコントロールのパターンがサポートされていない場合、実装、または null のいずれかを取得します。 カスタム NumericUpDown コントロールを設定して、範囲内の値になど、その[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]ピアを実装、 <xref:System.Windows.Automation.Provider.IRangeValueProvider>インターフェイスです。 例を次にどのようにピアの<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A>に応答するメソッドがオーバーライドされる、 <xref:System.Windows.Automation.Peers.PatternInterface?displayProperty=fullName>値。  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 A <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A>メソッドではパターン プロバイダーとしてのサブ要素を指定してもできます。 次のコードはどのように<xref:System.Windows.Controls.ItemsControl>転送は、内部のピアにパターンの処理をスクロール<xref:System.Windows.Controls.ScrollViewer>コントロールです。  
  
```csharp  
public override object GetPattern(PatternInterface patternInterface)  
{  
    if (patternInterface == PatternInterface.Scroll)  
    {  
        ItemsControl owner = (ItemsControl) base.Owner;  
  
        // ScrollHost is internal to the ItemsControl class  
        if (owner.ScrollHost != null)  
        {  
            AutomationPeer peer = UIElementAutomationPeer.CreatePeerForElement(owner.ScrollHost);  
            if ((peer != null) && (peer is IScrollProvider))  
            {  
                peer.EventsSource = this;  
                return (IScrollProvider) peer;  
            }  
        }  
    }  
    return base.GetPattern(patternInterface);  
}  
```  
  
```vb  
Public Class Class1  
    Public Overrides Function GetPattern(ByVal patternInterface__1 As PatternInterface) As Object  
        If patternInterface1 = PatternInterface.Scroll Then  
            Dim owner As ItemsControl = DirectCast(MyBase.Owner, ItemsControl)  
  
            ' ScrollHost is internal to the ItemsControl class  
            If owner.ScrollHost IsNot Nothing Then  
                Dim peer As AutomationPeer = UIElementAutomationPeer.CreatePeerForElement(owner.ScrollHost)  
                If (peer IsNot Nothing) AndAlso (TypeOf peer Is IScrollProvider) Then  
                    peer.EventsSource = Me  
                    Return DirectCast(peer, IScrollProvider)  
                End If  
            End If  
        End If  
        Return MyBase.GetPattern(patternInterface1)  
    End Function  
End Class  
```  
  
 このコード パターンの処理のためのサブ要素を指定するサブ要素オブジェクトを取得を使用してピアを作成、 <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A>メソッドでは、設定、 <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>を現在のピアでは、新しいピアのプロパティを新しいピアを返します。 設定<xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>サブ要素のサブ要素をオートメーション ピア ツリーに表示されると、サブ要素によって生成されるすべてのイベントを指定で指定したコントロールから発信されている<xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>します。 <xref:System.Windows.Controls.ScrollViewer>コントロールは、オートメーション ツリーには表示されずから発生したように、生成されるスクロールのイベントが表示されます、 <xref:System.Windows.Controls.ItemsControl>オブジェクトです。  
  
### <a name="override-core-methods"></a>"Core"メソッドをオーバーライドします。  
 自動化のサンプル コードでは、ピア クラスのパブリック メソッドを呼び出して、コントロールに関する情報を取得します。 コントロールに関する情報を提供するには、基本オートメーション ピア クラスで提供されているものとは異なり、コントロールの実装時に"Core"で終わる名前を持つ各メソッドをオーバーライドします。 少なくとも、コントロールを実装する必要があります、 <xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A>と<xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A>メソッドは、次の例で示すようにします。  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 実装<xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A>を返すことによって、コントロールの説明、 <xref:System.Windows.Automation.ControlType>値。 返すことができますが<xref:System.Windows.Automation.ControlType.Custom?displayProperty=fullName>コントロールを正確に記述されている場合より特定のコントロール型の&1; つ返す必要があります。 戻り値<xref:System.Windows.Automation.ControlType.Custom?displayProperty=fullName>を実装するプロバイダーの追加の作業が必要[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]、および[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]クライアント製品は、制御構造、キーボード操作、および使用できるコントロール パターンを予測することはできません。  
  
 実装、 <xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A>と<xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A>コントロールがデータの内容が含まれていますか (またはその両方) をユーザー インターフェイスで対話型のロールを満たすかどうかを示すメソッドです。 既定では、両方のメソッドが返す`true`します。 これらの設定には、オートメーション ツリーをフィルター処理するこれらのメソッドを使用するスクリーン リーダーなどの自動化ツールの使いやすさが向上します。 場合、 <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A>サブエレメント ピアに、サブ要素のピアの処理メソッド転送パターン<xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A>メソッドは、オートメーション ツリーからのサブ要素のピアを非表示にする場合は false で返すことができます。 スクロールなど、 <xref:System.Windows.Controls.ListBox>によって処理、 <xref:System.Windows.Controls.ScrollViewer>、およびのオートメーション ピア<xref:System.Windows.Automation.Peers.PatternInterface?displayProperty=fullName>によって返される、 <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A>のメソッド、 <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer>と関連付けられている、 <xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>します。そのため、 <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A>のメソッド、 <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer>を返します`false`れるため、 <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer>オートメーション ツリーがないです。  
  
 オートメーション ピアは、コントロールの適切な既定値を指定する必要があります。 注コントロールを参照する XAML を含めることによって、ピア実装の重要なメソッドをオーバーライドできます<xref:System.Windows.Automation.AutomationProperties>属性です。 たとえば、次の XAML がボタンをクリックし、2 つのカスタマイズを作成[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]プロパティです。  
  
```xaml  
<Button AutomationProperties.Name="Special"   
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>プロバイダーのパターンを実装します。  
 所有している要素から直接派生している場合に、カスタム プロバイダーによって実装されるインターフェイスが明示的に宣言される<xref:System.Windows.Controls.Control>します。 たとえば、次のコードがピアを宣言して、<xref:System.Windows.Controls.Control>範囲の値を実装します。  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 かどうかは所有しているコントロールから派生したコントロールの特定の種類など、 <xref:System.Windows.Controls.Primitives.RangeBase>ピアは、同等の派生ピア クラスから派生できます。 ここでは、ピアがから派生は<xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>の基本実装を提供する<xref:System.Windows.Automation.Provider.IRangeValueProvider>します。 次のコードでは、このようなピアの宣言を示します。  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
 、実装の例を参照してください。 [NumericUpDown カスタム コントロールおよびテーマと UI オートメーションのサポートのサンプル](http://go.microsoft.com/fwlink/?LinkID=160025)します。  
  
### <a name="raise-events"></a>イベントを発生させる  
 オートメーション クライアントは、オートメーション イベントをサブスクライブできます。 カスタム コントロールは、呼び出すことによってコントロールの状態に対する変更を報告する必要があります、 <xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A>メソッドです。 同様に、プロパティの値の変更されたときに呼び出す、 <xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A>メソッドです。 次のコードでは、コントロールのコード内からピア オブジェクトを取得し、イベントを発生させるメソッドを呼び出す方法を示します。 最適化の手法としては、コードは、この種類のイベントのリスナーがあるかどうかを判断します。 リスナーがある場合にのみイベントを発生させると、不要なオーバーヘッドを回避し、応答性を維持する制御に役立ちます。  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>関連項目  
 [UI オートメーションの概要](../../../../docs/framework/ui-automation/ui-automation-overview.md)   
 [NumericUpDown カスタム コントロールおよびテーマと UI オートメーションのサポートのサンプル](http://go.microsoft.com/fwlink/?LinkID=160025)   
 [サーバー側 UI オートメーション プロバイダーの実装](../../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)