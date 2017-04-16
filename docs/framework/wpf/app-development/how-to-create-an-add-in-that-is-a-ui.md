---
title: "方法 : UI であるアドインを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "作成 (UI であるアドインを) [WPF]"
  - "アドイン [WPF] UI"
  - "作成 (UI アドインを) [WPF]"
  - "UI アドイン [WPF] を作成します。"
  - "実装 (UI アドインを) [WPF]"
  - "アドインを作成するパイプライン セグメント [WPF]"
ms.assetid: 86375525-282b-4039-8352-8680051a10ea
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : UI であるアドインを作成する
\<?xml version="1.0" encoding="utf-8"?>
\<developerHowToDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>この例は、アドインを作成する方法を示しています、<token>グラス フレーム TLA</token> <token>では</token>によってホストされます、 <token>TLA2 拡張されたグラス</token>スタンドアロン アプリケーションです</para>。
    <para>、アドインは、 <token>TLA&#2;tla_ui</token>つまり、<token>グラス フレーム TLA2</token>ユーザー コントロールです。ユーザー コントロールのコンテンツは、1 つのボタンで、クリックすると、メッセージ ボックスを表示します。<token>グラス フレーム TLA2</token>スタンドアロン アプリケーションはアドインをホストする<token>TLA&#2;tla_ui</token>アプリケーションのメイン ウィンドウのコンテンツとして</para>。
    <para>
      <embeddedLabel>の前提条件</embeddedLabel>
    </para>
    <para>この例で強調表示、<token>グラス フレーム TLA2</token>の拡張機能、 <token>dnprdnshort</token>アドインでこのシナリオを実現し、モデルを以下を前提としています:</para>
    <list class="bullet">
      <listItem>
        <para>の知識、 <token>dnprdnshort</token>アドインなど、モデル パイプライン、アドインでは、ホストの開発用です。これらの概念に慣れていない場合は、次を参照してください。\<legacyLink xlink:href="8dd45b02-7218-40f9-857d-40d7b98b850b">アドインおよび拡張</legacyLink>します。パイプライン、アドイン、およびホスト アプリケーションの実装を説明するチュートリアルについては、次を参照してください\<legacyLink xlink:href="694a33c5-a040-450d-aed5-ac49fc88ce61">チュートリアル: 拡張性のあるアプリケーションを作成する</legacyLink>。</para> 。
      </listItem> 
      <listItem>
        <para>の知識、<token>グラス フレーム TLA2</token>の拡張機能、 <token>dnprdnshort</token>アドイン モデル、こちらをご覧: \<link xlink:href="00b4c776-29a8-4dba-b603-280a0cdc2ade">WPF アドインの概要</link>.</para>
      </listItem> 
    </list> 
  </introduction> 
  <codeExample> 
    <legacy> 
      <content>
        <para>がアドインを作成する、<token>グラス フレーム TLA2</token> <token>TLA&#2;tla_ui</token>各パイプライン セグメント、アドイン、およびホスト アプリケーションの特定のコードが必要です</para>。
        <para>
          <token>アウトラインの自動作成</token>
        </para>
      </content>
      <sections>
        <section address="Contract">
          <title>コントラクト パイプライン セグメントの実装</title>
          <content>
            <para>とアドインでは、 <token>TLA&#2;tla_ui</token>、アドインのコントラクトを実装する必要があります<codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>します。例では、 <codeInline>IWPFAddInContract</codeInline>実装<codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>の次のコードに示すようにします。</para>
            <code language="c#">using System.AddIn.Contract; // INativeHandleContract
using System.AddIn.Pipeline; // AddInContractAttribute

namespace Contracts
{
    /// &lt;summary&gt;
    /// Defines the services that an add-in will provide to a host application.
    /// In this case, the add-in is a UI.
    /// &lt;/summary&gt;
    [AddInContract]
    public interface IWPFAddInContract : INativeHandleContract {}
}</code>
          <code language="vb">Imports System.AddIn.Contract ' INativeHandleContract
Imports System.AddIn.Pipeline ' AddInContractAttribute

Namespace Contracts
    ''' &lt;summary&gt;
    ''' Defines the services that an add-in will provide to a host application.
    ''' In this case, the add-in is a UI.
    ''' &lt;/summary&gt;
    &lt;AddInContract&gt;
    Public Interface IWPFAddInContract
        Inherits INativeHandleContract
        Inherits IContract
    End Interface
End Namespace</code></content>
        </section>
        <section address="AddInViewPipeline">
          <title>アドインのビューのパイプライン セグメントの実装</title>
          <content>
            <para>のサブクラスとして、アドインに実装されるため、<codeEntityReference autoUpgrade="true">として</codeEntityReference>アドイン ビューの種類はサブクラス化も必要<codeEntityReference autoUpgrade="true">として</codeEntityReference>します。次のコードは、アドインのビューとして実装されたコントラクトの<codeInline>WPFAddInView</codeInline>クラス</para>
            <code language="c#">using System.AddIn.Pipeline; // AddInBaseAttribute
using System.Windows.Controls; // UserControl

namespace AddInViews
{
    /// &lt;summary&gt;
    /// Defines the add-in's view of the contract.
    /// &lt;/summary&gt;
    [AddInBase]
    public class WPFAddInView : UserControl { }
}</code> 
          <code language="vb">Imports System.AddIn.Pipeline ' AddInBaseAttribute
Imports System.Windows.Controls ' UserControl

Namespace AddInViews
    ''' &lt;summary&gt;
    ''' Defines the add-in's view of the contract.
    ''' &lt;/summary&gt;
    &lt;AddInBase&gt;
    Public Class WPFAddInView
        Inherits UserControl
    End Class
End Namespace</code>
            <para>ここでは、アドイン ビューがから派生した<codeEntityReference autoUpgrade="true">該当</codeEntityReference>します。そのため、アドインを<token>TLA&#2;tla_ui</token>からも派生する必要があります<codeEntityReference autoUpgrade="true">該当</codeEntityReference>します。</para>
          </content>
        </section>
        <section address="AddInSideAdapter">
          <title>Add-In-Side アダプター パイプライン セグメントの実装</title>
          <content>
            <para>コントラクトは、中に、 <codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>、アドインでは、<codeEntityReference autoUpgrade="true">として</codeEntityReference>(アドイン ビュー パイプライン セグメントで、指定された)。したがって、<codeEntityReference autoUpgrade="true">として</codeEntityReference>に変換する必要があります、 <codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>分離境界を越える前にします。呼び出して追加アドイン側アダプターでこの作業を行う<codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter(System.Windows.FrameworkElement)</codeEntityReference>次のコードに示すように、</para> 。
            <code language="c#">using System; // IntPtr
using System.AddIn.Contract; // INativeHandleContract
using System.AddIn.Pipeline; // AddInAdapterAttribute, FrameworkElementAdapters, ContractBase
using System.Security.Permissions;

using AddInViews; // WPFAddInView
using Contracts; // IWPFAddInContract

namespace AddInSideAdapters
{
    /// &lt;summary&gt;
    /// Adapts the add-in's view of the contract to the add-in contract
    /// &lt;/summary&gt;
    [AddInAdapter]
    public class WPFAddIn_ViewToContractAddInSideAdapter : ContractBase, IWPFAddInContract
    {
        WPFAddInView wpfAddInView;

        public WPFAddIn_ViewToContractAddInSideAdapter(WPFAddInView wpfAddInView)
        {
            // Adapt the add-in view of the contract (WPFAddInView) 
            // to the contract (IWPFAddInContract)
            this.wpfAddInView = wpfAddInView;
        }

        /// &lt;summary&gt;
        /// ContractBase.QueryContract must be overridden to:
        /// * Safely return a window handle for an add-in UI to the host 
        ///   application's application.
        /// * Enable tabbing between host application UI and add-in UI, in the
        ///   "add-in is a UI" scenario.
        /// &lt;/summary&gt;
        public override IContract QueryContract(string contractIdentifier)
        {
            if (contractIdentifier.Equals(typeof(INativeHandleContract).AssemblyQualifiedName))
            {
                return FrameworkElementAdapters.ViewToContractAdapter(this.wpfAddInView);
            }

            return base.QueryContract(contractIdentifier);
        }

        /// &lt;summary&gt;
        /// GetHandle is called by the WPF add-in model from the host application's 
        /// application domain to to get the window handle for an add-in UI from the 
        /// add-in's application domain. GetHandle is called if a window handle isn't 
        /// returned by other means ie overriding ContractBase.QueryContract, 
        /// as shown above.
        /// NOTE: This method requires UnmanagedCodePermission to be called 
        ///       (full-trust by default), to prevent illegal window handle
        ///       access in partially trusted scenarios. If the add-in could
        ///       run in a partially trusted application domain 
        ///       (eg AddInSecurityLevel.Internet), you can safely return a window
        ///       handle by overriding ContractBase.QueryContract, as shown above.
        /// &lt;/summary&gt;
        [SecurityPermissionAttribute(SecurityAction.Demand, Flags = SecurityPermissionFlag.UnmanagedCode)]
        public IntPtr GetHandle()
        {
            return FrameworkElementAdapters.ViewToContractAdapter(this.wpfAddInView).GetHandle();
        }
    }
}</code> 
          <code language="vb">Imports System ' IntPtr
Imports System.AddIn.Contract ' INativeHandleContract
Imports System.AddIn.Pipeline ' AddInAdapterAttribute, FrameworkElementAdapters, ContractBase
Imports System.Security.Permissions

Imports AddInViews ' WPFAddInView
Imports Contracts ' IWPFAddInContract

Namespace AddInSideAdapters
    ''' &lt;summary&gt;
    ''' Adapts the add-in's view of the contract to the add-in contract
    ''' &lt;/summary&gt;
    &lt;AddInAdapter&gt;
    Public Class WPFAddIn_ViewToContractAddInSideAdapter
        Inherits ContractBase
        Implements IWPFAddInContract

        Private wpfAddInView As WPFAddInView

        Public Sub New(ByVal wpfAddInView As WPFAddInView)
            ' Adapt the add-in view of the contract (WPFAddInView) 
            ' to the contract (IWPFAddInContract)
            Me.wpfAddInView = wpfAddInView
        End Sub

        ''' &lt;summary&gt;
        ''' ContractBase.QueryContract must be overridden to:
        ''' * Safely return a window handle for an add-in UI to the host 
        '''   application's application.
        ''' * Enable tabbing between host application UI and add-in UI, in the
        '''   "add-in is a UI" scenario.
        ''' &lt;/summary&gt;
        Public Overrides Function QueryContract(ByVal contractIdentifier As String) As IContract
            If contractIdentifier.Equals(GetType(INativeHandleContract).AssemblyQualifiedName) Then
                Return FrameworkElementAdapters.ViewToContractAdapter(Me.wpfAddInView)
            End If

            Return MyBase.QueryContract(contractIdentifier)
        End Function

        ''' &lt;summary&gt;
        ''' GetHandle is called by the WPF add-in model from the host application's 
        ''' application domain to to get the window handle for an add-in UI from the 
        ''' add-in's application domain. GetHandle is called if a window handle isn't 
        ''' returned by other means ie overriding ContractBase.QueryContract, 
        ''' as shown above.
        ''' NOTE: This method requires UnmanagedCodePermission to be called 
        '''       (full-trust by default), to prevent illegal window handle
        '''       access in partially trusted scenarios. If the add-in could
        '''       run in a partially trusted application domain 
        '''       (eg AddInSecurityLevel.Internet), you can safely return a window
        '''       handle by overriding ContractBase.QueryContract, as shown above.
        ''' &lt;/summary&gt;
        &lt;SecurityPermissionAttribute(SecurityAction.Demand, Flags:=SecurityPermissionFlag.UnmanagedCode)&gt;
        Public Function GetHandle() As IntPtr Implements INativeHandleContract.GetHandle
            Return FrameworkElementAdapters.ViewToContractAdapter(Me.wpfAddInView).GetHandle()
        End Function

    End Class
End Namespace</code> 
            <para>、アドインを返すモデルで、 <token>TLA&#2;tla_ui</token> (を参照してください\<link xlink:href="57f274b7-4c66-4b72-92eb-81939a393776">方法: UI 作成、アドインを返すこと</link>)、アドイン アダプタの変換、<codeEntityReference autoUpgrade="true">として</codeEntityReference>に、 <codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>を呼び出して<codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter(System.Windows.FrameworkElement)</codeEntityReference>します。<codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter(System.Windows.FrameworkElement)</codeEntityReference>からそれを呼び出すコードを記述するメソッドを実装する必要がありますが、このモデルでというもする必要があります。オーバーライドすることで、これを行う<codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.ContractBase.QueryContract(System.String)</codeEntityReference>を呼び出すコードを実装して<codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter(System.Windows.FrameworkElement)</codeEntityReference>場合を呼び出しているコード<codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.ContractBase.QueryContract(System.String)</codeEntityReference>を予期している、 <codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>します。この場合、呼び出し元は、後続のサブセクションで示されているホスト側アダプタになります。</para>
            <alert class="note">
              <para>オーバーライドすることも必要<codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.ContractBase.QueryContract(System.String)</codeEntityReference>ホスト アプリケーション間のタブ移動を有効にするには、このモデルで<token>TLA&#2;tla_ui</token>とアドインの<token>TLA&#2;tla_ui</token>します。詳細については、WPF アドインの制限事項」を参照してください\<link xlink:href="00b4c776-29a8-4dba-b603-280a0cdc2ade">WPF アドインの概要</link>.</para>
            </alert>
            <para>追加アドイン側アダプターから派生するインターフェイスを実装しているため<codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>を実装する必要があります<codeEntityReference autoUpgrade="true">M:System.AddIn.Contract.INativeHandleContract.GetHandle</codeEntityReference>これは無視されますが、ときに<codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.ContractBase.QueryContract(System.String)</codeEntityReference>がオーバーライドされます。</para>
          </content>
        </section>
        <section address="HostViewPipeline">
          <title>ホスト ビュー パイプライン セグメントの実装</title>
          <content>
            <para>このモデルでは、ホスト アプリケーション通常がホスト ビューに、<codeEntityReference autoUpgrade="true">として</codeEntityReference>サブクラスです。ホスト側アダプタに変換する必要があります、 <codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>に、<codeEntityReference autoUpgrade="true">として</codeEntityReference>後、 <codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>分離境界を超えています。メソッドを取得するホスト アプリケーションによって呼び出されるされていないため、<codeEntityReference autoUpgrade="true">として</codeEntityReference>、ホスト ビュー必要があります"return"、<codeEntityReference autoUpgrade="true">として</codeEntityReference>で示すことです。その結果、ホスト ビューがのサブクラスから派生する必要があります<codeEntityReference autoUpgrade="true">として</codeEntityReference>他を持つことができる<token>TLA&#2;tla_ui #plural</token>など<codeEntityReference autoUpgrade="true">該当</codeEntityReference>します。次のコードは、ホスト ビューとして実装されたコントラクトの<codeInline>WPFAddInHostView</codeInline>クラスです。</para>
            <code language="c#">using System.Windows.Controls; // UserControl

namespace HostViews
{
    /// &lt;summary&gt;
    /// Defines the host's view of the add-in
    /// &lt;/summary&gt;
    public class WPFAddInHostView : UserControl { }
}</code>
          <code language="vb">Imports System.Windows.Controls ' UserControl

Namespace HostViews
    ''' &lt;summary&gt;
    ''' Defines the host's view of the add-in
    ''' &lt;/summary&gt;
    Public Class WPFAddInHostView
        Inherits UserControl
    End Class
End Namespace</code>
          </content>
        </section>
        <section address="HostSideAdapter">
          <title>ホスト側アダプター パイプライン セグメントの実装</title>
          <content>
            <para>コントラクトは、中に、 <codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>、ホスト アプリケーションが必要ですが、<codeEntityReference autoUpgrade="true">項目に該当</codeEntityReference>(ホスト ビューで、指定した)。その結果、 <codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>に変換する必要があります、<codeEntityReference autoUpgrade="true">として</codeEntityReference>ホスト ビューのコンテンツとして設定する前に、分離境界を通過後 (から派生した<codeEntityReference autoUpgrade="true">該当</codeEntityReference>).</para>
            <para>の次のコードに示すように、ホスト側アダプターによってこの作業が実行されます。</para> 
            <code language="c#">using System.AddIn.Contract; // INativeHandleContract
using System.AddIn.Pipeline; // HostAdapterAttribute, FrameworkElementAdapters, ContractHandle
using System.Windows; // FrameworkElement

using Contracts; // IWPFAddInContract
using HostViews; // WPFAddInHostView

namespace HostSideAdapters
{
    /// &lt;summary&gt;
    /// Adapts the add-in contract to the host's view of the add-in
    /// &lt;/summary&gt;
    [HostAdapter]
    public class WPFAddIn_ContractToViewHostSideAdapter : WPFAddInHostView
    {
        IWPFAddInContract wpfAddInContract;
        ContractHandle wpfAddInContractHandle;

        public WPFAddIn_ContractToViewHostSideAdapter(IWPFAddInContract wpfAddInContract)
        {
            // Adapt the contract (IWPFAddInContract) to the host application's
            // view of the contract (WPFAddInHostView)
            this.wpfAddInContract = wpfAddInContract;

            // Prevent the reference to the contract from being released while the
            // host application uses the add-in
            this.wpfAddInContractHandle = new ContractHandle(wpfAddInContract);

            // Convert the INativeHandleContract for the add-in UI that was passed 
            // from the add-in side of the isolation boundary to a FrameworkElement
            string aqn = typeof(INativeHandleContract).AssemblyQualifiedName;
            INativeHandleContract inhc = (INativeHandleContract)wpfAddInContract.QueryContract(aqn);
            FrameworkElement fe = (FrameworkElement)FrameworkElementAdapters.ContractToViewAdapter(inhc);

            // Add FrameworkElement (which displays the UI provided by the add-in) as
            // content of the view (a UserControl)
            this.Content = fe;
        }
    }
}</code> 
          <code language="vb">Imports System.AddIn.Contract ' INativeHandleContract
Imports System.AddIn.Pipeline ' HostAdapterAttribute, FrameworkElementAdapters, ContractHandle
Imports System.Windows ' FrameworkElement

Imports Contracts ' IWPFAddInContract
Imports HostViews ' WPFAddInHostView

Namespace HostSideAdapters
    ''' &lt;summary&gt;
    ''' Adapts the add-in contract to the host's view of the add-in
    ''' &lt;/summary&gt;
    &lt;HostAdapter&gt;
    Public Class WPFAddIn_ContractToViewHostSideAdapter
        Inherits WPFAddInHostView
        Private wpfAddInContract As IWPFAddInContract
        Private wpfAddInContractHandle As ContractHandle

        Public Sub New(ByVal wpfAddInContract As IWPFAddInContract)
            ' Adapt the contract (IWPFAddInContract) to the host application's
            ' view of the contract (WPFAddInHostView)
            Me.wpfAddInContract = wpfAddInContract

            ' Prevent the reference to the contract from being released while the
            ' host application uses the add-in
            Me.wpfAddInContractHandle = New ContractHandle(wpfAddInContract)

            ' Convert the INativeHandleContract for the add-in UI that was passed 
            ' from the add-in side of the isolation boundary to a FrameworkElement
            Dim aqn As String = GetType(INativeHandleContract).AssemblyQualifiedName
            Dim inhc As INativeHandleContract = CType(wpfAddInContract.QueryContract(aqn), INativeHandleContract)
            Dim fe As FrameworkElement = CType(FrameworkElementAdapters.ContractToViewAdapter(inhc), FrameworkElement)

            ' Add FrameworkElement (which displays the UI provided by the add-in) as
            ' content of the view (a UserControl)
            Me.Content = fe
        End Sub
    End Class
End Namespace</code> 
            <para>、ホスト側アダプタを取得するよう、 <codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>を呼び出して追加アドイン側アダプターの<codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.ContractBase.QueryContract(System.String)</codeEntityReference>メソッド (これは、ポイントを<codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>分離境界を越える).</para>
            <para>ホスト側アダプターが次に、変換、 <codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>に、<codeEntityReference autoUpgrade="true">として</codeEntityReference>を呼び出して<codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter(System.AddIn.Contract.INativeHandleContract)</codeEntityReference>します。最後に、<codeEntityReference autoUpgrade="true">として</codeEntityReference>ホスト ビューのコンテンツとして設定します。</para>
          </content>
        </section>
        <section address="AddIn">
          <title>アドインを実装する</title>
          <content>
            <para>追加アドイン側アダプターとアドインのビューが用意で、アドインを実装できます、アドイン ビューから派生することで次のコードに示すようにします</para>。
            <code language="xaml">&lt;addInViews:WPFAddInView
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:addInViews="clr-namespace:AddInViews;assembly=AddInViews"
    x:Class="WPFAddIn1.AddInUI"&gt;

    &lt;Grid&gt;
        &lt;Button Click="clickMeButton_Click" Content="Click Me!" /&gt;        
    &lt;/Grid&gt;

&lt;/addInViews:WPFAddInView&gt;</code> 
            <code language="c#">using System.AddIn; // AddInAttribute
using System.Windows; // MessageBox, RoutedEventArgs

using AddInViews; // WPFAddInView

namespace WPFAddIn1
{
    /// &lt;summary&gt;
    /// Implements the add-in by deriving from WPFAddInView
    /// &lt;/summary&gt;
    [AddIn("WPF Add-In 1")]
    public partial class AddInUI : WPFAddInView
    {
        public AddInUI()
        {
            InitializeComponent();
        }

        void clickMeButton_Click(object sender, RoutedEventArgs e)
        {
            MessageBox.Show("Hello from WPFAddIn1");
        }
    }
}</code> 
          <code language="vb">Imports System.AddIn ' AddInAttribute
Imports System.Windows ' MessageBox, RoutedEventArgs

Imports AddInViews ' WPFAddInView

Namespace WPFAddIn1
    ''' &lt;summary&gt;
    ''' Implements the add-in by deriving from WPFAddInView
    ''' &lt;/summary&gt;
    &lt;AddIn("WPF Add-In 1")&gt;
    Partial Public Class AddInUI
        Inherits WPFAddInView
        Public Sub New()
            InitializeComponent()
        End Sub

        Private Sub clickMeButton_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)
            MessageBox.Show("Hello from WPFAddIn1")
        End Sub
    End Class
End Namespace</code>
            <para>からこの例では、このモデルの 1 つの興味深い利点を確認できます。 アドイン開発者はのみアドインを実装する必要があります (であるため、 <token>TLA&#2;tla_ui</token>も)、アドイン クラスとアドインの両方ではなく<token>TLA&#2;tla_ui</token>します。</para>
          </content>
        </section>
        <section address="HostApp">
          <title>ホスト アプリケーションを実装する</title>
          <content>
            <para>ホスト側アダプターとホスト ビューの作成、ホスト アプリケーションが使用できます、 <token>dnprdnshort</token>アドイン モデルでは、パイプラインを開き、アドインのホスト ビューを取得します。次の手順は、次のコードに表示されます。</para> 
            <code language="c#">// Get add-in pipeline folder (the folder in which this application was launched from)
string appPath = Environment.CurrentDirectory;

// Rebuild visual add-in pipeline
string[] warnings = AddInStore.Rebuild(appPath);
if (warnings.Length &gt; 0)
{
    string msg = "Could not rebuild pipeline:";
    foreach (string warning in warnings) msg += "\n" + warning;
    MessageBox.Show(msg);
    return;
}

// Activate add-in with Internet zone security isolation
Collection&lt;AddInToken&gt; addInTokens = AddInStore.FindAddIns(typeof(WPFAddInHostView), appPath);
AddInToken wpfAddInToken = addInTokens[0];
this.wpfAddInHostView = wpfAddInToken.Activate&lt;WPFAddInHostView&gt;(AddInSecurityLevel.Internet);

// Display add-in UI
this.addInUIHostGrid.Children.Add(this.wpfAddInHostView);</code> 
          <code language="vb">' Get add-in pipeline folder (the folder in which this application was launched from)
Dim appPath As String = Environment.CurrentDirectory

' Rebuild visual add-in pipeline
Dim warnings() As String = AddInStore.Rebuild(appPath)
If warnings.Length &gt; 0 Then
    Dim msg As String = "Could not rebuild pipeline:"
    For Each warning As String In warnings
        msg &amp;= vbLf &amp; warning
    Next warning
    MessageBox.Show(msg)
    Return
End If

' Activate add-in with Internet zone security isolation
Dim addInTokens As Collection(Of AddInToken) = AddInStore.FindAddIns(GetType(WPFAddInHostView), appPath)
Dim wpfAddInToken As AddInToken = addInTokens(0)
Me.wpfAddInHostView = wpfAddInToken.Activate(Of WPFAddInHostView)(AddInSecurityLevel.Internet)

' Display add-in UI
Me.addInUIHostGrid.Children.Add(Me.wpfAddInHostView)</code>
            <para>ホスト アプリケーションは標準的な<token>dnprdnshort</token>アドイン モデルではアクティブにするコード、アドインに暗黙的に、ホスト アプリケーションに、ホスト ビューを返します。その後、ホスト アプリケーションにはホスト ビューが表示されます (これは、<codeEntityReference autoUpgrade="true">該当</codeEntityReference>) から、<codeEntityReference autoUpgrade="true">テーブルを作成</codeEntityReference>.</para>
            <para>アドインとの対話を処理するためのコード<token>TLA&#2;tla_ui</token>アドインのアプリケーション ドメインで実行します。これらの対話には、次が含まれます:</para>
            <list class="bullet">
              <listItem>
                <para>処理、<codeEntityReference autoUpgrade="true">プロパティ</codeEntityReference> <codeEntityReference autoUpgrade="true">ここ</codeEntityReference>イベント</para>。
              </listItem> 
              <listItem>
                <para>を示す、<codeEntityReference autoUpgrade="true">実行</codeEntityReference>.</para>
              </listItem> 
            </list>
            <para>このアクティビティは、ホスト アプリケーションから完全に分離します。</para>
          </content>
        </section>
      </sections>
    </legacy>
  </codeExample>
  <relatedTopics>
\<legacyLink xlink:href="8dd45b02-7218-40f9-857d-40d7b98b850b">アドインと拡張</legacyLink>
\<link xlink:href="00b4c776-29a8-4dba-b603-280a0cdc2ade">WPF アドインの概要</link>
</relatedTopics>
</developerHowToDocument>
