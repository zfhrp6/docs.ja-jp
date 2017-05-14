---
title: ".NET Framework で互換性のために残されている型 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework 4.5, obsolete types
- types, obsolete in .NET Framework 4.5
- obsolete types [.NET Framework]
ms.assetid: e636d024-0fac-45eb-b721-25a8c0ceca8f
caps.latest.revision: 41
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 175e46e3729190423b85296d7c7c47b136339305
ms.contentlocale: ja-jp
ms.lasthandoff: 04/18/2017

---
# <a name="obsolete-types-in-the-net-framework"></a>.NET Framework で互換性のために残されている型
<a name="introduction"></a> この記事の表に、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] で互換性のために残されている型をアセンブリ別に示します。 各アセンブリで互換性のために残されている型と推奨される代替型の一覧を表示するには、以下のリンクを使用してください。 これらの型は廃止されているため、そのメンバーもすべて廃止されます。 .NET Framework クラス ライブラリで互換性のために残されているその他のメンバーの一覧については、[互換性のために残されているメンバー](../../../docs/framework/whats-new/obsolete-members.md)に関する記事をご覧ください。  
  
-   [互換性のために残されているシステム アセンブリの型](#obsolete_types_in_system_assemblies)  
  
    -   [mscorlib.dll](#mscorlib)  
  
    -   [System.Core.dll](#Core)  
  
    -   [System.Data.dll](#data)  
  
    -   [System.Data.OracleClient.dll](#oracleclient)  
  
    -   [System.Design.dll](#design)  
  
    -   [System.dll](#system)  
  
    -   [System.EnterpriseServices.dll](#enterpriseservices)  
  
    -   [System.Net.dll](#net)  
  
    -   [System.ServiceModel.dll](#servicemodel)  
  
    -   [System.Web.dll](#web)  
  
    -   [System.Web.Mobile.dll](#mobile)  
  
    -   [System.Workflow.Activities.dll](#workflow_activities)  
  
    -   [System.Workflow.ComponentModel.dll](#workflow_componentmodel)  
  
    -   [System.Workflow.Runtime.dll](#workflow_runtime)  
  
    -   [System.WorkflowServices.dll](#workflowservices)  
  
    -   [System.Xaml.dll](#xaml)  
  
    -   [System.Xml.dll](#xml)  
  
    -   [WindowsBase.dll](#WindowsBase)  
  
-   [互換性のために残されている Microsoft アセンブリの型](#obsolete_types_in_microsoft_assemblies)  
  
    -   [IEHost.dll and IEExec.exe](#IEHost)  
  
    -   [Microsoft.Build.Engine.dll](#Engine)  
  
    -   [Microsoft.JScript.dll](#jscript)  
  
    -   [Microsoft.VisualBasic.Compatibility.dll](#VBCompat)  
  
    -   [Microsoft.VisualBasic.Compatibility.Data.dll](#VBCompatData)  
  
    -   [Microsoft.VisualC.dll](#visualc)  
  
<a name="obsolete_types_in_system_assemblies"></a>   
## <a name="obsolete-types-in-system-assemblies"></a>互換性のために残されているシステム アセンブリの型  
 次の表に、システム アセンブリで、互換性のために残されていることが公表されている型を示します。 これらのアセンブリは、.NET Framework を対象とする汎用アプリケーションの開発で使用されます。  
  
<a name="mscorlib"></a>   
### <a name="assembly-mscorlibdll"></a>アセンブリ: mscorlib.dll  
  
|型|メッセージ|  
|----------|-------------|  
|<xref:System.ExecutionEngineException?displayProperty=fullName>|以前には、この型は、ランタイムで未定義の致命的なエラーを示していました。 ランタイムがこの例外を発生させることはなくなりましたが、この型は互換性のために残されています。|  
|<xref:System.Collections.CaseInsensitiveHashCodeProvider?displayProperty=fullName>|代わりに、<xref:System.StringComparer?displayProperty=fullName> を使用してください。|  
|<xref:System.Collections.IHashCodeProvider?displayProperty=fullName>|代わりに、<xref:System.Collections.IEqualityComparer?displayProperty=fullName> を使用してください。|  
|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=fullName>|<xref:System.Configuration.Assemblies.AssemblyHash> クラスの使用は推奨されていません。|  
|<xref:System.Diagnostics.Contracts.Internal.ContractHelper?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。 代わりに、System.Runtime.CompilerServices 名前空間の <xref:System.Runtime.CompilerServices.ContractHelper?displayProperty=fullName> クラスを使用してください。|  
|<xref:System.Reflection.Emit.UnmanagedMarshal?displayProperty=fullName>|代替 API を使用できます。代わりに、<xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> カスタム属性を生成してください。|  
|<xref:System.Runtime.InteropServices.BIND_OPTS?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.BIND_OPTS?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.BINDPTR?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.BINDPTR?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.CALLCONV?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.CALLCONV?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.CONNECTDATA?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.CONNECTDATA?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.DESCKIND?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.DESCKIND?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.DISPPARAMS?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.DISPPARAMS?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.ELEMDESC?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.ELEMDESC?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.EXCEPINFO?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.EXCEPINFO?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.FILETIME?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.FILETIME?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.FUNCDESC?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.FUNCDESC?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.FUNCFLAGS?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.FUNCFLAGS?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.FUNCKIND?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.FUNCKIND?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=fullName>|この属性の使用は推奨されていません。この属性は、将来のバージョンでは削除されます。|  
|<xref:System.Runtime.InteropServices.IDispatchImplType?displayProperty=fullName>|<xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=fullName> の使用は推奨されていません。|  
|<xref:System.Runtime.InteropServices.IDLDESC?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.IDLDESC?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.IDLFLAG?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.IDLFLAG?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.IMPLTYPEFLAGS?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.IMPLTYPEFLAGS?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.INVOKEKIND?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.INVOKEKIND?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.LIBFLAGS?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.LIBFLAGS?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.PARAMDESC?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.PARAMDESC?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.PARAMFLAG?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.PARAMFLAG?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.SetWin32ContextInIDispatchAttribute?displayProperty=fullName>|この属性は推奨されていません。 アプリケーション ドメインでは、IDispatch の呼び出しでアクティベーション コンテキスト境界は考慮されなくなりました。|  
|<xref:System.Runtime.InteropServices.STATSTG?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.STATSTG?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.SYSKIND?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.SYSKIND?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.TYPEATTR?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.TYPEATTR?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.TYPEDESC?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.TYPEDESC?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.TYPEFLAGS?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.TYPEFLAGS?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.TYPEKIND?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.TYPEKIND?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.TYPELIBATTR?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.TYPELIBATTR?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.UCOMIBindCtx?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.IBindCtx?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.UCOMIConnectionPoint?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.UCOMIConnectionPointContainer?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.UCOMIEnumConnectionPoints?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.IEnumConnectionPoints?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.UCOMIEnumConnections?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.IEnumConnections?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.UCOMIEnumMoniker?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.IEnumMoniker?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.UCOMIEnumString?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.IEnumString?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.UCOMIEnumVARIANT?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.UCOMIMoniker?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.IMoniker?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.UCOMIPersistFile?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.IPersistFile?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.UCOMIRunningObjectTable?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.IRunningObjectTable?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.UCOMIStream?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.UCOMITypeComp?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.ITypeComp?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.UCOMITypeInfo?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.UCOMITypeLib?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.ITypeLib?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.VARDESC?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.VARDESC?displayProperty=fullName> を使用してください。|  
|<xref:System.Runtime.InteropServices.VARFLAGS?displayProperty=fullName>|代わりに、<xref:System.Runtime.InteropServices.ComTypes.VARFLAGS?displayProperty=fullName> を使用してください。|  
|<xref:System.Security.SecurityCriticalScope?displayProperty=fullName>|<xref:System.Security.SecurityCriticalScope> は、.NET 2.0 の透過的な互換性のみを目的として使用されます。|  
|<xref:System.Security.SecurityTreatAsSafeAttribute?displayProperty=fullName>|<xref:System.Security.SecurityTreatAsSafeAttribute> は、.NET 2.0 の透過的な互換性のみを目的として使用されます。 代わりに、<xref:System.Security.SecuritySafeCriticalAttribute?displayProperty=fullName> を使用してください。|  
|<xref:System.Security.Policy.FirstMatchCodeGroup?displayProperty=fullName>|この型は互換性のために残されていますが、.NET Framework の将来のリリースでは削除されます。|  
|<xref:System.Security.Policy.PermissionRequestEvidence?displayProperty=fullName>|アセンブリ レベルの宣言セキュリティは互換性のために残されていますが、既定では、CLR によって強制されることはなくなりました。|  
|<xref:System.Security.Policy.UnionCodeGroup?displayProperty=fullName>|この型は互換性のために残されていますが、.NET Framework の将来のリリースでは削除されます。|  
  
 [ページのトップへ](#introduction)  
  
<a name="Core"></a>   
### <a name="assembly-systemcoredll"></a>アセンブリ: System.Core.dll  
  
|型|メッセージ|  
|----------|-------------|  
|<xref:System.Runtime.CompilerServices.ExecutionScope?displayProperty=fullName>|この型を使用すると、コンパイラ エラーが発生します。<br /><br /> この型は使用しないでください。|  
  
 [ページのトップへ](#introduction)  
  
<a name="data"></a>   
### <a name="assembly-systemdatadll"></a>アセンブリ: System.Data.dll  
  
|型|メッセージ|  
|----------|-------------|  
|<xref:System.Data.DataSysDescriptionAttribute?displayProperty=fullName>|<xref:System.Data.DataSysDescriptionAttribute> の使用は推奨されていません。|  
|<xref:System.Data.PropertyAttributes?displayProperty=fullName>|<xref:System.Data.PropertyAttributes> の使用は推奨されていません。|  
|<xref:System.Data.TypedDataSetGenerator?displayProperty=fullName>|<xref:System.Data.TypedDataSetGenerator> クラスは、将来のリリースでは削除されます。 System.Design.dll の <xref:System.Data.Design.TypedDataSetGenerator?displayProperty=fullName> を使用してください。|  
|<xref:System.Xml.XmlDataDocument?displayProperty=fullName>|<xref:System.Xml.XmlDataDocument> クラスは、将来のリリースでは削除されます。|  
  
 [ページのトップへ](#introduction)  
  
<a name="oracleclient"></a>   
### <a name="assembly-systemdataoracleclientdll"></a>アセンブリ: System.Data.OracleClient.dll  
  
|型|メッセージ|  
|----------|-------------|  
|<xref:System.Data.OracleClient.OracleClientFactory?displayProperty=fullName>|<xref:System.Data.OracleClient.OracleClientFactory> の使用は推奨されていません。|  
|<xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName>|<xref:System.Data.OracleClient.OracleCommand> の使用は推奨されていません。|  
|<xref:System.Data.OracleClient.OracleCommandBuilder?displayProperty=fullName>|<xref:System.Data.OracleClient.OracleCommandBuilder> の使用は推奨されていません。|  
|<xref:System.Data.OracleClient.OracleConnection?displayProperty=fullName>|<xref:System.Data.OracleClient.OracleConnection> の使用は推奨されていません。|  
|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=fullName>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder> の使用は推奨されていません。|  
|<xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>|<xref:System.Data.OracleClient.OracleDataAdapter> の使用は推奨されていません。|  
|<xref:System.Data.OracleClient.OraclePermission?displayProperty=fullName>|<xref:System.Data.OracleClient.OraclePermission> の使用は推奨されていません。|  
|<xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=fullName>|<xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=fullName> の使用は推奨されていません。|  
  
 [ページのトップへ](#introduction)  
  
<a name="design"></a>   
### <a name="assembly-systemdesigndll"></a>アセンブリ: System.Design.dll  
  
|型|メッセージ|  
|----------|-------------|  
|<xref:System.ComponentModel.Design.LocalizationExtenderProvider?displayProperty=fullName>|このクラスの使用は推奨されていません。 代わりに、<xref:System.ComponentModel.Design.Serialization.CodeDomLocalizationProvider?displayProperty=fullName> を使用してください。|  
|<xref:System.Web.UI.Design.DataBindingCollectionConverter?displayProperty=fullName>|データ バインディングの編集は、プロパティ グリッドではなく、<xref:System.ComponentModel.Design.DesignerActionList?displayProperty=fullName> から起動されるので、この型の使用は推奨されていません。|  
|<xref:System.Web.UI.Design.DataBindingCollectionEditor?displayProperty=fullName>|データ バインディングの編集は、プロパティ グリッドではなく、<xref:System.ComponentModel.Design.DesignerActionList?displayProperty=fullName> から起動されるので、この型の使用は推奨されていません。|  
|<xref:System.Web.UI.Design.IControlDesignerBehavior?displayProperty=fullName>|別の方法として、<xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=fullName> および <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=fullName> を使用することをお勧めします。|  
|<xref:System.Web.UI.Design.IHtmlControlDesignerBehavior?displayProperty=fullName>|別の方法として、<xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=fullName> および <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=fullName> を使用することをお勧めします。|  
|<xref:System.Web.UI.Design.ITemplateEditingFrame?displayProperty=fullName>|テンプレート編集は <xref:System.Web.UI.Design.ControlDesigner?displayProperty=fullName> で処理されるので、この型の使用は推奨されていません。 テンプレート編集をサポートするには、<xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=fullName> プロパティのテンプレート データを公開して、<xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=fullName> を呼び出します。|  
|<xref:System.Web.UI.Design.IWebFormReferenceManager?displayProperty=fullName>|別の方法として、<xref:System.Web.UI.Design.WebFormsReferenceManager?displayProperty=fullName> を使用することをお勧めします。 <xref:System.Web.UI.Design.WebFormsReferenceManager> は機能が追加されており、さらに機能を拡張できます。 <xref:System.Web.UI.Design.WebFormsReferenceManager> を取得するには、<xref:System.Web.UI.Design.ControlDesigner?displayProperty=fullName> から `RootDesigner.ReferenceManager` プロパティを使用します。|  
|<xref:System.Web.UI.Design.IWebFormsDocumentService?displayProperty=fullName>|別の方法として、<xref:System.Web.UI.Design.WebFormsRootDesigner?displayProperty=fullName> を使用することをお勧めします。 <xref:System.Web.UI.Design.WebFormsRootDesigner> は機能が追加されており、さらに機能を拡張できます。 <xref:System.Web.UI.Design.WebFormsRootDesigner> を取得するには、<xref:System.Web.UI.Design.ControlDesigner?displayProperty=fullName> から <xref:System.Web.UI.Design.ControlDesigner.RootDesigner%2A> プロパティを使用します。|  
|<xref:System.Web.UI.Design.ITemplateEditingService?displayProperty=fullName>|テンプレート編集は <xref:System.Web.UI.Design.ControlDesigner?displayProperty=fullName> で処理されるので、この型の使用は推奨されていません。 テンプレート編集をサポートするには、<xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=fullName> プロパティのテンプレート データを公開して、<xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=fullName> を呼び出します。|  
|<xref:System.Web.UI.Design.ReadWriteControlDesigner?displayProperty=fullName>|別の方法として、コンテンツの編集に <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=fullName> が使用されるので、<xref:System.Web.UI.Design.ContainerControlDesigner?displayProperty=fullName> を使用することをお勧めします。 デザイナーの各領域を使用すると、編集する対象のコンテンツの制御を強化できます。|  
|<xref:System.Web.UI.Design.TemplateEditingService?displayProperty=fullName>|テンプレート編集は <xref:System.Web.UI.Design.ControlDesigner?displayProperty=fullName> で処理されるので、この型の使用は推奨されていません。 テンプレート編集をサポートするには、<xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=fullName> プロパティのテンプレート データを公開して、<xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=fullName> を呼び出します。|  
|<xref:System.Web.UI.Design.TemplateEditingVerb?displayProperty=fullName>|テンプレート編集は <xref:System.Web.UI.Design.ControlDesigner?displayProperty=fullName> で処理されるので、この型の使用は推奨されていません。 テンプレート編集をサポートするには、<xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=fullName> プロパティのテンプレート データを公開して、<xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=fullName> を呼び出します。|  
|<xref:System.Web.UI.Design.WebControls.CalendarAutoFormatDialog?displayProperty=fullName>|[オートフォーマット] ダイアログ ボックスはデザイナー ホストによって起動されるので、この型の使用は推奨されていません。 使用できる [オートフォーマット] の一覧は、<xref:System.Web.UI.Design.ControlDesigner.AutoFormats%2A?displayProperty=fullName> プロパティの <xref:System.Web.UI.Design.ControlDesigner?displayProperty=fullName> で公開されています。|  
|<xref:System.Web.UI.Design.WebControls.PanelDesigner?displayProperty=fullName>|別の方法として、コンテンツの編集に <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=fullName> が使用されるので、<xref:System.Web.UI.Design.WebControls.PanelContainerDesigner?displayProperty=fullName> を使用することをお勧めします。 デザイナーの各領域を使用すると、編集する対象のコンテンツの制御を強化できます。|  
  
 [ページのトップへ](#introduction)  
  
<a name="system"></a>   
### <a name="assembly-systemdll"></a>アセンブリ: System.dll  
  
|型|メッセージ|  
|----------|-------------|  
|<xref:System.ComponentModel.IComNativeDescriptorHandler?displayProperty=fullName>|このインターフェイスの使用は推奨されていません。 代わりに、<xref:System.ComponentModel.TypeDescriptionProvider?displayProperty=fullName> をハンドル型 <xref:System.ComponentModel.TypeDescriptor.ComObjectType%2A?displayProperty=fullName> に追加します。|  
|<xref:System.ComponentModel.RecommendedAsConfigurableAttribute?displayProperty=fullName>|新しい設定モデルを操作するには、代わりに、<xref:System.ComponentModel.SettingsBindableAttribute?displayProperty=fullName> を使用してください。|  
|<xref:System.ComponentModel.Design.Serialization.RootDesignerSerializerAttribute?displayProperty=fullName>|この属性は推奨されていません。 代わりに、<xref:System.ComponentModel.Design.Serialization.DesignerSerializerAttribute?displayProperty=fullName> を使用してください。 たとえば、CodeDom のルート デザイナーを指定するには、`DesignerSerializerAttribute\(...,typeof\(TypeCodeDomSerializer\)\)` を使用します。|  
|<xref:System.Diagnostics.DiagnosticsConfigurationHandler?displayProperty=fullName>|このクラスの使用は推奨されていません。|  
|<xref:System.Diagnostics.PerformanceCounterManager?displayProperty=fullName>|このクラスの使用は推奨されていません。 代わりに、<xref:System.Diagnostics.PerformanceCounter?displayProperty=fullName> クラスからパフォーマンス カウンターを使用してください。|  
|<xref:System.Net.GlobalProxySelection?displayProperty=fullName>|このクラスの使用は推奨されていません。 グローバルな既定のプロキシにアクセスして設定するには、代わりに、<xref:System.Net.WebRequest.DefaultWebProxy%2A?displayProperty=fullName> を使用してください。 <xref:System.Net.GlobalProxySelection.GetEmptyWebProxy%2A?displayProperty=fullName> の代わりに、"null" を使用してください。|  
|<xref:System.Net.Sockets.SocketClientAccessPolicyProtocol?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> この型を使用すると、コンパイラ エラーが発生します。<br /><br /> この API は、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。|  
  
 [ページのトップへ](#introduction)  
  
<a name="enterpriseservices"></a>   
### <a name="assembly-systementerpriseservicesdll"></a>アセンブリ: System.EnterpriseServices.dll  
  
|型|メッセージ|  
|----------|-------------|  
|<xref:System.EnterpriseServices.RegistrationHelperTx?displayProperty=fullName>|<xref:System.EnterpriseServices.RegistrationHelperTx> クラスの使用は推奨されていません。|  
  
 [ページのトップへ](#introduction)  
  
<a name="net"></a>   
### <a name="assembly-systemnetdll"></a>アセンブリ: System.Net.dll  
  
|型|メッセージ|  
|----------|-------------|  
|<xref:System.Net.INetworkProgress?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> この型を使用すると、コンパイラ エラーが発生します。<br /><br /> この API は、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。|  
|<xref:System.Net.IUnsafeWebRequestCreate?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> この型を使用すると、コンパイラ エラーが発生します。<br /><br /> この API は、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。|  
|<xref:System.Net.NetworkProgressChangedEventArgs?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> この型を使用すると、コンパイラ エラーが発生します。<br /><br /> この API は、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。|  
|<xref:System.Net.UiSynchronizationContext?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> この型を使用すると、コンパイラ エラーが発生します。<br /><br /> この API は、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。|  
|<xref:System.Net.Sockets.HttpPolicyDownloaderProtocol?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> この型を使用すると、コンパイラ エラーが発生します。<br /><br /> この API は、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。|  
|<xref:System.Net.Sockets.SecurityCriticalAction?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> この型を使用すると、コンパイラ エラーが発生します。<br /><br /> この API は、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。|  
|<xref:System.Net.Sockets.SocketPolicy?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> この型を使用すると、コンパイラ エラーが発生します。<br /><br /> この API は、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。|  
|<xref:System.Net.Sockets.UdpAnySourceMulticastClient?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> この型を使用すると、コンパイラ エラーが発生します。<br /><br /> この API は、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。|  
|<xref:System.Net.Sockets.UdpSingleSourceMulticastClient?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> この型を使用すると、コンパイラ エラーが発生します。<br /><br /> この API は、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。|  
  
 [ページのトップへ](#introduction)  
  
<a name="servicemodel"></a>   
### <a name="assembly-systemservicemodeldll"></a>アセンブリ: System.ServiceModel.dll  
  
|種類|メッセージ|  
|----------|-------------|  
|<xref:System.ServiceModel.NetPeerTcpBinding?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> ピア チャネルの機能は互換性のために残されていますが、今後削除される予定です。|  
|<xref:System.ServiceModel.Channels.HttpCookieContainerBindingElement?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> この型は互換性のために残されています。 Http <xref:System.Net.CookieContainer> を有効にするには、Http バインドか <xref:System.ServiceModel.Channels.HttpTransportBindingElement> で `AllowCookies` プロパティを使用します。|  
|<xref:System.ServiceModel.Channels.PeerCustomResolverBindingElement?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> ピア チャネルの機能は互換性のために残されていますが、今後削除される予定です。|  
|<xref:System.ServiceModel.Channels.PeerTransportBindingElement?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> ピア チャネルの機能は互換性のために残されていますが、今後削除される予定です。|  
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingCollectionElement?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> ピア チャネルの機能は互換性のために残されていますが、今後削除される予定です。|  
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> ピア チャネルの機能は互換性のために残されていますが、今後削除される予定です。|  
|<xref:System.ServiceModel.Configuration.PeerTransportElement?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> ピア チャネルの機能は互換性のために残されていますが、今後削除される予定です。|  
|<xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> ピア チャネルの機能は互換性のために残されていますが、今後削除される予定です。|  
  
 [ページのトップへ](#introduction)  
  
<a name="web"></a>   
### <a name="assembly-systemwebdll"></a>アセンブリ: System.Web.dll  
  
|型|メッセージ|  
|----------|-------------|  
|<xref:System.Web.Configuration.PassportAuthentication?displayProperty=fullName>|この型は互換性のために残されています。 パスポート認証製品はサポート対象から除外され、[Microsoft アカウント](http://go.microsoft.com/fwlink/?LinkId=733413)に置き換えられました。|  
|<xref:System.Web.Mail.MailAttachment?displayProperty=fullName>|別の方法として、<xref:System.Net.Mail.Attachment?displayProperty=fullName> を使用することをお勧めします。|  
|<xref:System.Web.Mail.MailEncoding?displayProperty=fullName>|別の方法として、<xref:System.Net.Mime.TransferEncoding?displayProperty=fullName> を使用することをお勧めします。|  
|<xref:System.Web.Mail.MailFormat?displayProperty=fullName>|別の方法として、<xref:System.Net.Mail.MailMessage.IsBodyHtml%2A?displayProperty=fullName> を使用することをお勧めします。|  
|<xref:System.Web.Mail.MailMessage?displayProperty=fullName>|別の方法として、<xref:System.Net.Mail.MailMessage?displayProperty=fullName> を使用することをお勧めします。|  
|<xref:System.Web.Mail.MailPriority?displayProperty=fullName>|別の方法として、<xref:System.Net.Mail.MailPriority?displayProperty=fullName> を使用することをお勧めします。|  
|<xref:System.Web.Mail.SmtpMail?displayProperty=fullName>|別の方法として、<xref:System.Net.Mail.SmtpClient?displayProperty=fullName> を使用することをお勧めします。|  
|<xref:System.Web.Security.PassportAuthenticationEventArgs?displayProperty=fullName>|この型は互換性のために残されています。 パスポート認証製品はサポート対象から除外され、[Microsoft アカウント](http://go.microsoft.com/fwlink/?LinkId=733413)に置き換えられました。|  
|<xref:System.Web.Security.PassportAuthenticationEventHandler?displayProperty=fullName>|この型は互換性のために残されています。 パスポート認証製品はサポート対象から除外され、[Microsoft アカウント](http://go.microsoft.com/fwlink/?LinkId=733413)に置き換えられました。|  
|<xref:System.Web.Security.PassportAuthenticationModule?displayProperty=fullName>|この型は互換性のために残されています。 パスポート認証製品はサポート対象から除外され、[Microsoft アカウント](http://go.microsoft.com/fwlink/?LinkId=733413)に置き換えられました。|  
|<xref:System.Web.Security.PassportIdentity?displayProperty=fullName>|この型は互換性のために残されています。 パスポート認証製品はサポート対象から除外され、[Microsoft アカウント](http://go.microsoft.com/fwlink/?LinkId=733413)に置き換えられました。|  
|<xref:System.Web.Security.PassportPrincipal?displayProperty=fullName>|この型は互換性のために残されています。 パスポート認証製品はサポート対象から除外され、[Microsoft アカウント](http://go.microsoft.com/fwlink/?LinkId=733413)に置き換えられました。|  
|<xref:System.Web.UI.ObjectConverter?displayProperty=fullName>|別の方法として、<xref:System.Convert?displayProperty=fullName> および <xref:System.String.Format%2A?displayProperty=fullName> を使用することをお勧めします。|  
  
 [ページのトップへ](#introduction)  
  
<a name="mobile"></a>   
### <a name="assembly-systemwebmobiledll"></a>アセンブリ: System.Web.Mobile.dll  
  
|種類|メッセージ|  
|----------|-------------|  
|<xref:System.Web.Mobile.CookielessData?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.Mobile.DeviceFilterElement?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.Mobile.DeviceFilterElementCollection?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.Mobile.DeviceFiltersSection?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.Mobile.ErrorHandlerModule?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.Mobile.MobileCapabilities?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.Mobile.MobileDeviceCapabilitiesSectionHandler?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.Mobile.MobileErrorInfo?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.Mobile.MobileFormsAuthentication?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.Design.MobileControls.IMobileDesigner?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.Design.MobileControls.IMobileWebFormServices?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.Design.MobileControls.MobileResource?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.Design.MobileControls.Converters.DataFieldConverter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.Design.MobileControls.Converters.DataMemberConverter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.AdRotator?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Alignment?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ArrayListCollectionBase?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.BaseValidator?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.BooleanOption?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Calendar?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Command?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.CommandFormat?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.CompareValidator?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Constants?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ControlElement?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ControlElementCollection?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ControlPager?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.CustomValidator?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.DesignerAdapterAttribute?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.DeviceElement?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.DeviceElementCollection?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.DeviceOverridableAttribute?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.DeviceSpecific?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoice?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceCollection?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceControlBuilder?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateBuilder?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateContainer?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificControlBuilder?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ErrorFormatterPage?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.FontInfo?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.FontSize?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Form?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.FormControlBuilder?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.FormMethod?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.IControlAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Image?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.IObjectListFieldCollection?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.IPageAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ItemPager?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ITemplateable?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Label?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Link?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.List?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ListCommandEventArgs?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ListCommandEventHandler?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ListControlBuilder?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ListDataBindEventArgs?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ListDataBindEventHandler?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ListDecoration?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ListSelectType?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.LiteralLink?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.LiteralText?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.LiteralTextContainerControlBuilder?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.LiteralTextControlBuilder?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.LoadItemsEventArgs?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.LoadItemsEventHandler?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.MobileControl?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.MobileControlBuilder?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.MobileControlsSection?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.MobileControlsSectionHandler?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.MobileListItem?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.MobileListItemCollection?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.MobileListItemType?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.MobilePage?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.MobileTypeNameConverter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.MobileUserControl?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ObjectList?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ObjectListCommand?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ObjectListCommandCollection?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventArgs?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventHandler?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ObjectListControlBuilder?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventArgs?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventHandler?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ObjectListField?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ObjectListFieldCollection?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ObjectListItem?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ObjectListItemCollection?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventArgs?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventHandler?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventArgs?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventHandler?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ObjectListTitleAttribute?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ObjectListViewMode?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.PagedControl?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.PagerStyle?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Panel?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.PanelControlBuilder?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.PersistNameAttribute?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.PhoneCall?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.RangeValidator?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.RegularExpressionValidator?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.RequiredFieldValidator?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.SelectionList?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Style?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.StyleSheet?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.StyleSheetControlBuilder?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.TemplateContainer?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.TextBox?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.TextBoxControlBuilder?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.TextControl?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.TextView?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.TextViewElement?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.ValidationSummary?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Wrapping?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCalendarAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCommandAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlFormAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlImageAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlLinkAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlMobileTextWriter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPageAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPhoneCallAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlSelectionListAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlTextBoxAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.ControlAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCalendarAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCommandAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlControlAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlFormAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlImageAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLabelAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLinkAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlListAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLiteralTextAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlMobileTextWriter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlObjectListAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPageAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPanelAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPhoneCallAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlSelectionListAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextBoxAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextViewAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidationSummaryAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidatorAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.MobileTextWriter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.MultiPartWriter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlMobileTextWriter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlPageAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlCalendarAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlCommandAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlControlAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlFormAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlImageAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlLabelAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlLinkAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlListAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlLiteralTextAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlMobileTextWriter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlObjectListAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlPageAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlPanelAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlPhoneCallAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlPostFieldType?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlSelectionListAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextBoxAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextViewAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidationSummaryAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidatorAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.Doctype?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.StyleSheetLocation?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCalendarAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCommandAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlControlAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCssHandler?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlFormAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlImageAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLabelAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLinkAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlListAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLiteralTextAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlMobileTextWriter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlObjectListAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPageAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPanelAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPhoneCallAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlSelectionListAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextBoxAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextViewAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidationSummaryAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidatorAdapter?displayProperty=fullName>|System.Web.Mobile.dll アセンブリの使用は推奨されていません。今後は使用しないでください。 ASP.NET モバイル アプリケーションを開発する方法については、[モバイル向け ASP.NET](http://go.microsoft.com/fwlink/?LinkId=157231) に関するページをご覧ください。|  
  
 [ページのトップへ](#introduction)  
  
<a name="workflow_activities"></a>   
### <a name="assembly-systemworkflowactivitiesdll"></a>アセンブリ: System.Workflow.Activities.dll  
  
|型|メッセージ|  
|----------|-------------|  
|<xref:System.Workflow.Activities?displayProperty=fullName> 名前空間のすべての型|最初に .NET Framework 4.5 で廃止されました。<br /><br /> System.Workflow.\* 型の使用は推奨されていません。 代わりに、<xref:System.Activities>.\* の新しい型を使用してください。|  
|<xref:System.Workflow.Activities.Configuration.ActiveDirectoryRoleFactoryConfiguration?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> System.Workflow.\* 型の使用は推奨されていません。 代わりに、<xref:System.Activities>.\* の新しい型を使用してください。|  
|<xref:System.Workflow.Activities.Rules.RuleActionTrackingEvent?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> System.Workflow.\* 型の使用は推奨されていません。 代わりに、<xref:System.Activities>.\* の新しい型を使用してください。|  
|<xref:System.Workflow.Activities.Rules.RuleConditionReference?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> System.Workflow.\* 型の使用は推奨されていません。 代わりに、<xref:System.Activities>.\* の新しい型を使用してください。|  
|<xref:System.Workflow.Activities.Rules.RuleSetReference?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> System.Workflow.\* 型の使用は推奨されていません。 代わりに、<xref:System.Activities>.\* の新しい型を使用してください。|  
  
 [ページのトップへ](#introduction)  
  
<a name="workflow_componentmodel"></a>   
### <a name="assembly-systemworkflowcomponentmodeldll"></a>アセンブリ: System.Workflow.ComponentModel.dll  
  
|型|メッセージ|  
|----------|-------------|  
|<xref:System.Workflow.ComponentModel.GetValueOverride?displayProperty=fullName> と <xref:System.Workflow.ComponentModel.SetValueOverride?displayProperty=fullName> を除く <xref:System.Workflow.ComponentModel> 名前空間のすべての型|最初に .NET Framework 4.5 で廃止されました。<br /><br /> System.Workflow.\* 型の使用は推奨されていません。 代わりに、<xref:System.Activities>.\* の新しい型を使用してください。|  
|<xref:System.Workflow.ComponentModel.Compiler.ValidationError?displayProperty=fullName> と <xref:System.Workflow.ComponentModel.Compiler.ValidationErrorCollection?displayProperty=fullName> を除く <xref:System.Workflow.ComponentModel.Compiler> 名前空間のすべての型|最初に .NET Framework 4.5 で廃止されました。<br /><br /> System.Workflow.\* 型の使用は推奨されていません。 代わりに、<xref:System.Activities>.\* の新しい型を使用してください。|  
|<xref:System.Workflow.ComponentModel.Design.ConnectorEventHandler> を除く <xref:System.Workflow.ComponentModel.Design> 名前空間のすべての型|最初に .NET Framework 4.5 で廃止されました。<br /><br /> System.Workflow.\* 型の使用は推奨されていません。 代わりに、<xref:System.Activities>.\* の新しい型を使用してください。|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializationManager?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> System.Workflow.\* 型の使用は推奨されていません。 代わりに、<xref:System.Activities>.\* の新しい型を使用してください。|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializer?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> System.Workflow.\* 型の使用は推奨されていません。 代わりに、<xref:System.Activities>.\* の新しい型を使用してください。|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivityMarkupSerializer?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> System.Workflow.\* 型の使用は推奨されていません。 代わりに、<xref:System.Activities>.\* の新しい型を使用してください。|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivitySurrogateSelector?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> System.Workflow.\* 型の使用は推奨されていません。 代わりに、<xref:System.Activities>.\* の新しい型を使用してください。|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivityTypeCodeDomSerializer?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> System.Workflow.\* 型の使用は推奨されていません。 代わりに、<xref:System.Activities>.\* の新しい型を使用してください。|  
|<xref:System.Workflow.ComponentModel.Serialization.CompositeActivityMarkupSerializer?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> System.Workflow.\* 型の使用は推奨されていません。 代わりに、<xref:System.Activities>.\* の新しい型を使用してください。|  
|<xref:System.Workflow.ComponentModel.Serialization.DependencyObjectCodeDomSerializer?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> System.Workflow.\* 型の使用は推奨されていません。 代わりに、<xref:System.Activities>.\* の新しい型を使用してください。|  
  
 [ページのトップへ](#introduction)  
  
<a name="workflow_runtime"></a>   
### <a name="assembly-systemworkflowruntimedll"></a>アセンブリ: System.Workflow.Runtime.dll  
  
|型|メッセージ|  
|----------|-------------| 
|System.Activities.Statements.Interop](assetId:///T:System.Activities.Statements.Interop)|最初に .NET Framework 4.5 で廃止されました。<br /><br />Workflow Foundation 3.0 の型の使用は推奨されていません。 代わりに、<xref:System.Activities>.\* の Workflow 4.0 の型を使用してください。|  
|<xref:System.Activities.Tracking.InteropTrackingRecord>|最初に .NET Framework 4.5 で廃止されました。<br /><br />Workflow Foundation 3.0 の型の使用は推奨されていません。 代わりに、<xref:System.Activities>.\* の Workflow 4.0 の型を使用してください。|   
|<xref:System.Workflow.Runtime> 名前空間のすべての型|最初に .NET Framework 4.5 で廃止されました。<br /><br /> System.Workflow.\* 型の使用は推奨されていません。 代わりに、<xref:System.Activities>.\* の新しい型を使用してください。|  
|<xref:System.Workflow.Runtime.Configuration> 名前空間のすべての型|最初に .NET Framework 4.5 で廃止されました。<br /><br /> System.Workflow.\* 型の使用は推奨されていません。 代わりに、<xref:System.Activities>.\* の新しい型を使用してください。|  
|<xref:System.Workflow.Runtime.DebugEngine.DebugEngineCallback> を除く <xref:System.Workflow.Runtime.DebugEngine> 名前空間のすべての型|最初に .NET Framework 4.5 で廃止されました。<br /><br /> System.Workflow.\* 型の使用は推奨されていません。 代わりに、<xref:System.Activities>.\* の新しい型を使用してください。|  
|<xref:System.Workflow.Runtime.Hosting.WorkflowCommitWorkBatchService.CommitWorkBatchCallback> を除く <xref:System.Workflow.Runtime.Hosting> 名前空間のすべての型|最初に .NET Framework 4.5 で廃止されました。<br /><br /> System.Workflow.\* 型の使用は推奨されていません。 代わりに、<xref:System.Activities>.\* の新しい型を使用してください。|  
|<xref:System.Workflow.Runtime.Tracking> 名前空間のすべての型|最初に .NET Framework 4.5 で廃止されました。<br /><br /> System.Workflow.\* 型の使用は推奨されていません。 代わりに、<xref:System.Activities>.\* の新しい型を使用してください。|  
  
 [ページのトップへ](#introduction)  
  
<a name="workflowservices"></a>   
### <a name="assembly-systemworkflowservicesdll"></a>アセンブリ: System.WorkflowServices.dll  
  
|型|メッセージ|  
|----------|-------------|  
|<xref:System.ServiceModel.WorkflowServiceHost?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> WF 3 の型は廃止されました。 代わりに、<xref:System.Activities>.\* の新しい WF 4 の型を使用してください。|  
|<xref:System.ServiceModel.Activation.WorkflowServiceHostFactory?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> WF 3 の型は廃止されました。 代わりに、<xref:System.Activities>.\* の新しい WF 4 の型を使用してください。|  
|<xref:System.ServiceModel.Activities.Description.WorkflowRuntimeEndpoint?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> WF 3 の型は廃止されました。 代わりに、<xref:System.Activities>.\* の新しい WF 4 の型を使用してください。|  
|<xref:System.ServiceModel.Configuration.ExtendedWorkflowRuntimeServiceElementCollection?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> WF 3 の型は廃止されました。 代わりに、<xref:System.Activities>.\* の新しい WF 4 の型を使用してください。|  
|<xref:System.ServiceModel.Configuration.PersistenceProviderElement?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> WF 3 の型は廃止されました。 代わりに、<xref:System.Activities>.\* の新しい WF 4 の型を使用してください。|  
|<xref:System.ServiceModel.Configuration.WorkflowRuntimeElement?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> WF 3 の型は廃止されました。 代わりに、<xref:System.Activities>.\* の新しい WF 4 の型を使用してください。|  
|<xref:System.ServiceModel.Description.DurableOperationAttribute?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> WF 3 の型は廃止されました。 代わりに、<xref:System.Activities>.\* の新しい WF 4 の型を使用してください。|  
|<xref:System.ServiceModel.Description.DurableServiceAttribute?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> WF 3 の型は廃止されました。 代わりに、<xref:System.Activities>.\* の新しい WF 4 の型を使用してください。|  
|<xref:System.ServiceModel.Description.PersistenceProviderBehavior?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> WF 3 の型は廃止されました。 代わりに、<xref:System.Activities>.\* の新しい WF 4 の型を使用してください。|  
|<xref:System.ServiceModel.Description.UnknownExceptionAction?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> WF 3 の型は廃止されました。 代わりに、<xref:System.Activities>.\* の新しい WF 4 の型を使用してください。|  
|<xref:System.ServiceModel.Description.WorkflowRuntimeBehavior?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> WF 3 の型は廃止されました。 代わりに、<xref:System.Activities>.\* の新しい WF 4 の型を使用してください。|  
|<xref:System.ServiceModel.Dispatcher.DurableOperationContext?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> WF 3 の型は廃止されました。 代わりに、<xref:System.Activities>.\* の新しい WF 4 の型を使用してください。|  
|<xref:System.ServiceModel.Persistence.InstanceLockException?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> WF 3 の型は廃止されました。 代わりに、<xref:System.Activities>.\* の新しい WF 4 の型を使用してください。|  
|<xref:System.ServiceModel.Persistence.InstanceNotFoundException?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> WF 3 の型は廃止されました。 代わりに、<xref:System.Activities>.\* の新しい WF 4 の型を使用してください。|  
|<xref:System.ServiceModel.Persistence.LockingPersistenceProvider?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> WF 3 の型は廃止されました。 代わりに、<xref:System.Activities>.\* の新しい WF 4 の型を使用してください。|  
|<xref:System.ServiceModel.Persistence.PersistenceException?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> WF 3 の型は廃止されました。 代わりに、<xref:System.Activities>.\* の新しい WF 4 の型を使用してください。|  
|<xref:System.ServiceModel.Persistence.PersistenceProvider?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> WF 3 の型は廃止されました。 代わりに、<xref:System.Activities>.\* の新しい WF 4 の型を使用してください。|  
|<xref:System.ServiceModel.Persistence.PersistenceProviderFactory?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> WF 3 の型は廃止されました。 代わりに、<xref:System.Activities>.\* の新しい WF 4 の型を使用してください。|  
|<xref:System.ServiceModel.Persistence.SqlPersistenceProviderFactory?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> WF 3 の型は廃止されました。 代わりに、<xref:System.Activities>.\* の新しい WF 4 の型を使用してください。|  
|<xref:System.Workflow.Activities?displayProperty=fullName> 名前空間のすべての型|最初に .NET Framework 4.5 で廃止されました。<br /><br /> WF 3 の型は廃止されました。 代わりに、<xref:System.Activities>.\* の新しい WF 4 の型を使用してください。|  
|<xref:System.Workflow.Runtime.Hosting.ChannelManagerService?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> WF 3 の型は廃止されました。 代わりに、<xref:System.Activities>.\* の新しい WF 4 の型を使用してください。|  
  
 [ページのトップへ](#introduction)  
  
<a name="xaml"></a>   
### <a name="assembly-systemxamldll"></a>アセンブリ: System.Xaml.dll  
  
|種類|メッセージ|  
|----------|-------------|  
|<xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute?displayProperty=fullName>|これは、XAML パーサーでは使用されなくなりました。 <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute?displayProperty=fullName> を参照してください。|  
  
 [ページのトップへ](#introduction)  
  
<a name="xml"></a>   
### <a name="assembly-systemxmldll"></a>アセンブリ: System.Xml.dll  
  
|型|メッセージ|  
|----------|-------------|  
|<xref:System.Xml.IApplicationResourceStreamResolver?displayProperty=fullName>|最初に .NET Framework 4.5 で廃止されました。<br /><br /> この型を使用すると、コンパイラ エラーが発生します。<br /><br /> この API は、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。|  
|<xref:System.Xml.Schema.XmlSchemaCollection?displayProperty=fullName>|スキーマ コンパイルおよび検証には、<xref:System.Xml.Schema.XmlSchemaSet?displayProperty=fullName> を使用してください。|  
|<xref:System.Xml.XmlValidatingReader?displayProperty=fullName>|代わりに、適切な <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> を使用する <xref:System.Xml.XmlReader.Create%2A?displayProperty=fullName> メソッドによって作成された <xref:System.Xml.XmlReader?displayProperty=fullName> を使用してください。|  
|<xref:System.Xml.XmlXapResolver?displayProperty=fullName>|この型を使用すると、コンパイラ エラーが発生します。 この API は、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。|  
|<xref:System.Xml.Xsl.XslTransform?displayProperty=fullName>|このクラスの使用は推奨されていません。 代わりに、<xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=fullName> を使用してください。|  
  
 [ページのトップへ](#introduction)  
  
<a name="WindowsBase"></a>   
### <a name="assembly-windowsbasedll"></a>アセンブリ: WindowsBase.dll  
  
|型|メッセージ|  
|----------|-------------|  
|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=fullName>|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=fullName> の使用は推奨されていません。 このインターフェイスは、使用されなくなりました。|  
  
 [ページのトップへ](#introduction)  
  
<a name="obsolete_types_in_microsoft_assemblies"></a>   
## <a name="obsolete-types-in-microsoft-assemblies"></a>互換性のために残されている Microsoft アセンブリの型  
 以下のセクションで、互換性のために残されている Microsoft アセンブリの型を示します。 これらのアセンブリは、個別の言語 (たとえば、Microsoft.JScript.dll や Microsoft.VisualC.dll) を対象とした特殊な目的のアセンブリです。  
  
<a name="IEHost"></a>   
### <a name="assembly-iehostdll-and-ieexecexe"></a>アセンブリ: IEHost.dll and IEExec.exe  
 IEHost.dll および IEExec.exe アセンブリは .NET Framework から削除されています。 これらのアセンブリのすべての型およびメンバーは廃止され、[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ではサポートされていません。 これらのアセンブリは Internet Explorer で Windows フォーム コントロールをホストし、実行可能ファイルを実行するために使用されていました。 代替手段としては、ClickOnce、XAML ブラウザー アプリケーション (XBAP)、および Microsoft Silverlight をお勧めします。  
  
 [ページのトップへ](#introduction)  
  
<a name="Engine"></a>   
### <a name="assembly-microsoftbuildenginedll"></a>アセンブリ: Microsoft.Build.Engine.dll  
  
|型|メッセージ|  
|----------|-------------|  
|<xref:Microsoft.Build.BuildEngine.Engine?displayProperty=fullName>|このクラスの使用は推奨されていません。 代わりに、<!--zz <xref:Microsoft.Build?displayProperty=fullName> -->`Microsoft.Build` アセンブリの <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=fullName> を使用してください。|  
|<xref:Microsoft.Build.BuildEngine.Project?displayProperty=fullName>|このクラスの使用は推奨されていません。 代わりに、<xref:Microsoft.Build?displayProperty=fullName> アセンブリの <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=fullName> を使用してください。|  
  
 [ページのトップへ](#introduction)  
  
<a name="jscript"></a>   
### <a name="assembly-microsoftjscriptdll"></a>アセンブリ: Microsoft.JScript.dll  
  
|型|メッセージ|  
|----------|-------------|  
|<xref:Microsoft.JScript.Vsa.BaseVsaEngine?displayProperty=fullName>|この型の使用は推奨されていません。Visual Studio 2005 の時点から使用は推奨されておらず、これに代わる機能はありません。 詳細については、<xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> のドキュメントを参照してください。|  
|<xref:Microsoft.JScript.Vsa.BaseVsaSite?displayProperty=fullName>|この型の使用は推奨されていません。Visual Studio 2005 の時点から使用は推奨されておらず、これに代わる機能はありません。 詳細については、<xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> のドキュメントを参照してください。|  
|<xref:Microsoft.JScript.Vsa.BaseVsaStartup?displayProperty=fullName>|この型の使用は推奨されていません。Visual Studio 2005 の時点から使用は推奨されておらず、これに代わる機能はありません。 詳細については、<xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> のドキュメントを参照してください。|  
|<xref:Microsoft.JScript.Vsa.IJSVsaCodeItem?displayProperty=fullName>|この型の使用は推奨されていません。Visual Studio 2005 の時点から使用は推奨されておらず、これに代わる機能はありません。 詳細については、<xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> のドキュメントを参照してください。|  
|<xref:Microsoft.JScript.Vsa.IJSVsaEngine?displayProperty=fullName>|この型の使用は推奨されていません。Visual Studio 2005 の時点から使用は推奨されておらず、これに代わる機能はありません。 詳細については、<xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> のドキュメントを参照してください。|  
|<xref:Microsoft.JScript.Vsa.IJSVsaError?displayProperty=fullName>|この型の使用は推奨されていません。Visual Studio 2005 の時点から使用は推奨されておらず、これに代わる機能はありません。 詳細については、<xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> のドキュメントを参照してください。|  
|<xref:Microsoft.JScript.Vsa.IJSVsaGlobalItem?displayProperty=fullName>|この型の使用は推奨されていません。Visual Studio 2005 の時点から使用は推奨されておらず、これに代わる機能はありません。 詳細については、<xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> のドキュメントを参照してください。|  
|<xref:Microsoft.JScript.Vsa.IJSVsaItem?displayProperty=fullName>|この型の使用は推奨されていません。Visual Studio 2005 の時点から使用は推奨されておらず、これに代わる機能はありません。 詳細については、<xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> のドキュメントを参照してください。|  
|<xref:Microsoft.JScript.Vsa.IJSVsaItems?displayProperty=fullName>|この型の使用は推奨されていません。Visual Studio 2005 の時点から使用は推奨されておらず、これに代わる機能はありません。 詳細については、<xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> のドキュメントを参照してください。|  
|<xref:Microsoft.JScript.Vsa.IJSVsaPersistSite?displayProperty=fullName>|この型の使用は推奨されていません。Visual Studio 2005 の時点から使用は推奨されておらず、これに代わる機能はありません。 詳細については、<xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> のドキュメントを参照してください。|  
|<xref:Microsoft.JScript.Vsa.IJSVsaReferenceItem?displayProperty=fullName>|この型の使用は推奨されていません。Visual Studio 2005 の時点から使用は推奨されておらず、これに代わる機能はありません。 詳細については、<xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> のドキュメントを参照してください。|  
|<xref:Microsoft.JScript.Vsa.IJSVsaSite?displayProperty=fullName>|この型の使用は推奨されていません。Visual Studio 2005 の時点から使用は推奨されておらず、これに代わる機能はありません。 詳細については、<xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> のドキュメントを参照してください。|  
|<xref:Microsoft.JScript.Vsa.JSVsaError?displayProperty=fullName>|この型の使用は推奨されていません。Visual Studio 2005 の時点から使用は推奨されておらず、これに代わる機能はありません。 詳細については、<xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> のドキュメントを参照してください。|  
|<xref:Microsoft.JScript.Vsa.JSVsaException?displayProperty=fullName>|この型の使用は推奨されていません。Visual Studio 2005 の時点から使用は推奨されておらず、これに代わる機能はありません。 詳細については、<xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> のドキュメントを参照してください。|  
|<xref:Microsoft.JScript.Vsa.JSVsaItemFlag?displayProperty=fullName>|この型の使用は推奨されていません。Visual Studio 2005 の時点から使用は推奨されておらず、これに代わる機能はありません。 詳細については、<xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> のドキュメントを参照してください。|  
|<xref:Microsoft.JScript.Vsa.JSVsaItemType?displayProperty=fullName>|この型の使用は推奨されていません。Visual Studio 2005 の時点から使用は推奨されておらず、これに代わる機能はありません。 詳細については、<xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> のドキュメントを参照してください。|  
|<xref:Microsoft.JScript.Vsa.ResInfo?displayProperty=fullName>|この型の使用は推奨されていません。Visual Studio 2005 の時点から使用は推奨されておらず、これに代わる機能はありません。 詳細については、<xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> のドキュメントを参照してください。|  
|<xref:Microsoft.JScript.Vsa.VsaEngine?displayProperty=fullName>|この型の使用は推奨されていません。Visual Studio 2005 の時点から使用は推奨されておらず、これに代わる機能はありません。 詳細については、<xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=fullName> のドキュメントを参照してください。|  
  
 [ページのトップへ](#introduction)  
  
<a name="VBCompat"></a>   
### <a name="assembly-microsoftvisualbasiccompatibilitydll"></a>アセンブリ: Microsoft.VisualBasic.Compatibility.dll  
  
|型|メッセージ|  
|----------|-------------|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseControlArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseOcxArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ButtonArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CheckBoxArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CheckedListBoxArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ColorDialogArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ComboBoxArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DirListBox?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DirListBoxArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DriveListBox?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DriveListBoxArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FileListBox?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FileListBoxArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FixedLengthString?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FontDialogArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FormShowConstants?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.GroupBoxArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.HScrollBarArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ImageListArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.LabelArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListBoxArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListBoxItem?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListViewArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.LoadResConstants?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MaskedTextBoxArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MenuItemArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MouseButtonConstants?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.OpenFileDialogArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PanelArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PictureBoxArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PrintDialogArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ProgressBarArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.RadioButtonArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.RichTextBoxArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.SaveFileDialogArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ScaleMode?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ShiftConstants?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.StatusBarArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.StatusStripArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.Support?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TabControlArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TextBoxArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TimerArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolBarArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolStripArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolStripMenuItemArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TreeViewArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.VScrollBarArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebBrowserArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClass?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassContainingClassNotOptional?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassCouldNotFindEvent?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassNextItemCannotBeCurrentWebItem?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassNextItemRespondNotFound?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassUserWebClassNameNotOptional?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassWebClassFileNameNotOptional?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassWebItemNotValid?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItem?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemAssociatedWebClassNotOptional?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemClosingTagNotFound?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemCouldNotLoadEmbeddedResource?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemCouldNotLoadTemplateFile?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemNameNotOptional?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemNoTemplateSpecified?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemTooManyNestedTags?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemUnexpectedErrorReadingTemplateFile?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ZOrderConstants?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
  
 [ページのトップへ](#introduction)  
  
<a name="VBCompatData"></a>   
### <a name="assembly-microsoftvisualbasiccompatibilitydatadll"></a>アセンブリ: Microsoft.VisualBasic.Compatibility.Data.dll  
  
|型|メッセージ|  
|----------|-------------|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.BOFActionEnum?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.EndOfRecordsetDelegate?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.EOFActionEnum?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.ErrorDelegate?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FetchCompleteDelegate?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FetchProgressDelegate?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FieldChangeCompleteDelegate?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.MoveCompleteDelegate?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.OrientationEnum?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.RecordChangeCompleteDelegate?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.RecordsetChangeCompleteDelegate?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeFieldDelegate?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeRecordDelegate?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeRecordsetDelegate?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillMoveDelegate?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODCArray?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseDataEnvironment?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BindingCollectionEnumerator?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CONNECTDATA?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBBINDING?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBCOLUMNINFO?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBID?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBinding?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBindingCollection?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBKINDENUM?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBPROPIDSET?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IAccessor?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IChapteredRowset?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IColumnsInfo?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IConnectionPoint?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IConnectionPointContainer?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IDataFormat?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IDataFormatDisp?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IEnumConnectionPoints?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IEnumConnections?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowPosition?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowPositionChange?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowset?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetChange?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetIdentity?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetInfo?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetNotify?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MBinding?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MBindingCollection?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.SRDescriptionAttribute?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UGUID?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UNAME?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UpdateMode?displayProperty=fullName>|「[Microsoft.VisualBasic.Compatibility.VB6.\<member> は互換性のために残され、32 ビット プロセス内でのみサポートされる](https://msdn.microsoft.com/library/ee839621.aspx)」をご覧ください。|  
  
 [ページのトップへ](#introduction)  
  
<a name="visualc"></a>   
### <a name="assembly-microsoftvisualcdll"></a>アセンブリ: Microsoft.VisualC.dll  
  
|型|メッセージ|  
|----------|-------------|  
|<xref:Microsoft.VisualC.DebugInfoInPDBAttribute?displayProperty=fullName>|Microsoft.VisualC.dll は互換性のために残されているアセンブリであり、下位互換性のためだけに存在します。|  
|<xref:Microsoft.VisualC.DecoratedNameAttribute?displayProperty=fullName>|Microsoft.VisualC.dll は互換性のために残されているアセンブリであり、下位互換性のためだけに存在します。|  
|<xref:Microsoft.VisualC.IsConstModifier?displayProperty=fullName>|Microsoft.VisualC.dll は互換性のために残されているアセンブリであり、下位互換性のためだけに存在します。|  
|<xref:Microsoft.VisualC.IsCXXReferenceModifier?displayProperty=fullName>|Microsoft.VisualC.dll は互換性のために残されているアセンブリであり、下位互換性のためだけに存在します。|  
|<xref:Microsoft.VisualC.IsLongModifier?displayProperty=fullName>|Microsoft.VisualC.dll は互換性のために残されているアセンブリであり、下位互換性のためだけに存在します。|  
|<xref:Microsoft.VisualC.IsSignedModifier?displayProperty=fullName>|Microsoft.VisualC.dll は互換性のために残されているアセンブリであり、下位互換性のためだけに存在します。|  
|<xref:Microsoft.VisualC.IsVolatileModifier?displayProperty=fullName>|Microsoft.VisualC.dll は互換性のために残されているアセンブリであり、下位互換性のためだけに存在します。|  
|<xref:Microsoft.VisualC.MiscellaneousBitsAttribute?displayProperty=fullName>|Microsoft.VisualC.dll は互換性のために残されているアセンブリであり、下位互換性のためだけに存在します。|  
|<xref:Microsoft.VisualC.NeedsCopyConstructorModifier?displayProperty=fullName>|Microsoft.VisualC.dll は互換性のために残されているアセンブリであり、下位互換性のためだけに存在します。|  
|<xref:Microsoft.VisualC.NoSignSpecifiedModifier?displayProperty=fullName>|Microsoft.VisualC.dll は互換性のために残されているアセンブリであり、下位互換性のためだけに存在します。|  
  
## <a name="see-also"></a>関連項目  
 [クラス ライブラリの互換性のために残されている機能](../../../docs/framework/whats-new/whats-obsolete.md)   
 [互換性のために残されているメンバー](../../../docs/framework/whats-new/obsolete-members.md)
