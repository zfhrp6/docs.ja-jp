---
title: "メソッド アクセスの保護 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "コード セキュリティ, メソッド アクセス"
  - "メソッド アクセスのセキュリティ"
  - "安全なコーディング, メソッド アクセス"
  - "セキュリティ [.NET Framework], メソッド アクセス"
ms.assetid: f7c2d6ec-3b18-4e0e-9991-acd97189d818
caps.latest.revision: 16
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# メソッド アクセスの保護
信頼関係のない任意のコードに呼び出しを許可することが不適切なメソッドがあります。 このようなメソッドは、制限された情報を提供する、渡された任意の情報を信頼する、パラメーターのエラー チェックを行わない、誤ったパラメーターを受け取って正しく機能しないかなんらかの被害をもたらすなどの、いくつかの危険性をもたらします。 これらのケースを認識し、メソッドを保護するために役立つ措置を講じる必要があります。  
  
 パブリックでの使用を目的としていないメソッドをパブリックとして使用する場合は、メソッドを制限する必要があることがあります。 たとえば、独自の DLL 経由で呼び出すインターフェイスはパブリックにする必要があります。しかし、顧客がそのインターフェイスを使用したり、悪意のあるコードがコンポーネントへのエントリ ポイントとして攻略したりするのを防ぐために、そのインターフェイスをパブリックとして公開しない場合があります。 また、パブリックではあるものの、パブリック使用を想定していないメソッドを制限する一般的な理由として、非常に内部的なインターフェイスで、ドキュメントを残したり、サポートするのを避けたりする場合も考えられます。  
  
> [!CAUTION]
>  コード アクセス セキュリティと部分的に信頼できるコード  
>   
>  .NET Framework には、コード アクセス セキュリティ \(CAS\) と呼ばれる、同一アプリケーションで実行される各種コードにさまざまな信頼レベルを強制的に適用するメカニズムが備わっています。  .NET Framework におけるコード アクセス セキュリティを、部分的に信頼できるコード、特に発生元の不明なコードのセキュリティ境界として使用しないでください。 発生元の不明なコードの読み込みと実行に関しては、他のセキュリティ対策を適切に導入することなく行わないようにしてください。  
>   
>  このポリシーは .NET Framework のすべてのバージョンに適用されますが、Silverlight に含まれる .NET Framework には適用されません。  
  
 マネージ コードには、メソッド アクセスを制限するいくつかの方法があります。  
  
-   クラス、アセンブリ、派生クラスが信頼されている場合は、これらへのアクセシビリティのスコープを制限します。 これが、メソッド アクセスを制限する最も簡単な方法です。 派生クラスが親クラスの ID を共有することがありますが、一般的に、派生クラスは派生元のクラスよりも信頼度が低くなる可能性があります。 特に、キーワード **protected** からは信頼を推測しないでください。セキュリティ コンテキストでは、このキーワードの使用は必須ではありません。  
  
-   指定した ID の呼び出し元だけにメソッド アクセスを制限します。基本的には、選択した特定の[証拠](http://msdn.microsoft.com/ja-jp/64ceb7c8-a0b4-46c4-97dc-6c22da0539da) \(厳密な名前、発行者、ゾーンなど\) に限定します。  
  
-   選択したアクセス許可を持つ呼び出し元だけにメソッド アクセスを制限します。  
  
 同様に、宣言セキュリティを使用すると、クラスの継承を制御できます。 以下を実行する場合は **InheritanceDemand** を使用します。  
  
-   派生したクラスに、特定の ID またはアクセス許可を要求します。  
  
-   特定のメソッドをオーバーライドする派生クラスに、特定の ID またはアクセス許可を要求します。  
  
 呼び出し元に特定の厳密な名前による署名を要求することによってアクセスを制限し、パブリック クラスの保護に役立つ方法の例を次に示します。 この例では、厳密な名前を要求する **Demand** と共に <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> を使用しています。 アセンブリを厳密な名前で署名する方法のタスク ベースの情報については、「[厳密な名前付きアセンブリの作成と使用](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)」を参照してください。  
  
```vb  
<StrongNameIdentityPermissionAttribute(SecurityAction.Demand, PublicKey := "…hex…", Name := "App1", Version := "0.0.0.0")>  _ Public Class Class1 End Class  
  
```  
  
```csharp  
[StrongNameIdentityPermissionAttribute(SecurityAction.Demand, PublicKey="…hex…", Name="App1", Version="0.0.0.0")] public class Class1 { }   
```  
  
## クラスとメンバーを信頼関係のないコードが使用できないようにする  
 このセクションで示す宣言を使用すると、特定のクラスとメソッド、およびプロパティとイベントが部分的な信頼のコードによって使用されるのを防ぐことができます。 これらの宣言をクラスに適用すると、すべてのメソッド、プロパティ、イベントが保護されますが、フィールドへのアクセスは宣言セキュリティの影響を受けないため、注意が必要です。 また、リンク確認要求は直前の呼び出し元に対して保護できるようにするだけで、攻撃を受ける可能性が残っています。  
  
> [!NOTE]
>  [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] では、新しい透過性モデルが導入されました。[透過的セキュリティ コード、レベル 2](../../../docs/framework/misc/security-transparent-code-level-2.md) モデルでは、<xref:System.Security.SecurityCriticalAttribute> 属性によって安全なコードを識別します。 セキュリティ クリティカル コードでは、呼び出し元と継承先の両方が完全に信頼されていることが必要です。 .NET Framework の以前のバージョンのコード アクセス セキュリティ規則で実行されているアセンブリは、レベル 2 のアセンブリを呼び出すことができます。 この場合、セキュリティ クリティカル属性は、完全な信頼のためのリンク確認要求として扱われます。  
  
 厳密な名前付きアセンブリでは、パブリックにアクセスされるすべてのメソッド、プロパティ、イベントに [LinkDemand](../../../docs/framework/misc/link-demands.md) が適用され、完全に信頼されている呼び出し元だけに使用を制限できます。 この機能を無効にするには、<xref:System.Security.AllowPartiallyTrustedCallersAttribute> 属性を適用する必要があります。 このため、信頼関係のない呼び出し元を除外するクラスを明示的に指定することは、署名のないアセンブリまたはこの属性を持つアセンブリだけに必要です。これらの宣言を使用して、信頼関係のない呼び出し元からの利用を想定していない型のサブセットをマークできます。  
  
 クラスおよびメンバーを信頼関係のないコードによって使用されるのを防ぐ方法の例を次に示します。  
  
 パブリックの非シール クラスの場合:  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _ System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _ Public Class CanDeriveFromMe End Class  
  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")] [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")] public class CanDeriveFromMe { }  
```  
  
 パブリックのシール クラスの場合:  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _ NotInheritable Public Class CannotDeriveFromMe End Class  
  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")] public sealed class CannotDeriveFromMe { }  
```  
  
 パブリックの抽象クラスの場合:  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _ System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _ MustInherit Public Class CannotCreateInstanceOfMe_CanCastToMe End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")] [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")] public abstract class CannotCreateInstanceOfMe_CanCastToMe{}  
```  
  
 パブリックの仮想関数の場合:  
  
```vb  
Class Base1 <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _ Public Overridable Sub CanOverrideOrCallMe() End Sub 'CanOverrideOrCallMe End Class 'Base1  
```  
  
```csharp  
class Base1 { [System.Security.Permissions.PermissionSetAttribute( System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")] [System.Security.Permissions.PermissionSetAttribute( System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")] public virtual void CanOverrideOrCallMe() {} }  
```  
  
 パブリックの抽象関数の場合:  
  
```vb  
MustInherit Class Base2 <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _ Public Sub MustOverrideMe() End Sub End Class 'Base2  
```  
  
```csharp  
abstract class Base2{ [System.Security.Permissions.PermissionSetAttribute( System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")] [System.Security.Permissions.PermissionSetAttribute( System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")] public abstract void MustOverrideMe(); }  
```  
  
 基本クラスが完全な信頼を確認要求しない、パブリック オーバーライド関数の場合:  
  
```vb  
Class Derived Inherits Base1 <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.Demand, Name:="FullTrust")> _ Public Overrides Sub CanOverrideOrCallMe() MyBase.CanOverrideOrCallMe() End Sub 'CanOverrideOrCallMe End Class 'Derived  
```  
  
```csharp  
class Derived : Base1 { [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.Demand, Name="FullTrust")] public override void CanOverrideOrCallMe() { base.CanOverrideOrCallMe(); } }  
```  
  
 基本クラスが完全な信頼を確認要求する、パブリック オーバーライド関数の場合:  
  
```vb  
Class Derived Inherits Base1 <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _ Public Overrides Sub CanOverrideOrCallMe() MyBase.CanOverrideOrCallMe() End Sub 'CanOverrideOrCallMe End Class 'Derived  
```  
  
```csharp  
class Derived : Base1 { [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")] public override void CanOverrideOrCallMe() { base.CanOverrideOrCallMe(); } }  
```  
  
 パブリック インターフェイスの場合:  
  
```vb  
Public Interface ICanCastToMe <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust")> _ Sub CanImplementMe() End Interface 'ICanCastToMe <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust")> _ Class Implemented Implements ICanCastToMe Public Sub CanImplementMe() End Sub 'CanImplementMe  
```  
  
```csharp  
public interface ICanCastToMe { [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")] [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")] void CanImplementMe(); } [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")] [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")] class Implemented : ICanCastToMe { public void CanImplementMe() { } }  
```  
  
## Virtual Internal Overrides または Overloads Overridable Friend  
  
> [!NOTE]
>  このセクションではメソッドを `virtual` と `internal` の両方 \(Visual Basic の `Overloads``Overridable``Friend`\) として宣言するときのセキュリティの問題に関する注意事項について説明します。 この注意事項の対象となるのは .NET Framework バージョン 1.0 および 1.1 のみで、バージョン 2.0 は対象になりません。  
  
 .NET Framework バージョン 1.0 および 1.1 では、コードを他のアセンブリから使用できないようにする場合、型システムのアクセシビリティの微妙な点を知っておく必要があります。**virtual** および **internal** \(Visual Basic では **Overloads Overridable Friend**\) が宣言されたメソッドは、親クラスの vtable エントリをオーバーライドでき、internal なので同じアセンブリ内だけで使用できます。 しかし、オーバーライドのアクセシビリティは **virtual** キーワードによって決められ、他のアセンブリがクラス自身へアクセスできる限り、そのアセンブリによってこれがオーバーライドされる可能性があります。 オーバーライドの可能性に問題がある場合は、宣言セキュリティを使用してそれを修正するか、**virtual** キーワードが厳密には必要ないときは、このキーワードを削除します。  
  
 ある言語コンパイラがコンパイル エラーによってこれらのオーバーライドを防いだとしても、他のコンパイラによって記述されたコードがオーバーライドする可能性があります。  
  
## 参照  
 [安全なコーディングのガイドライン](../../../docs/standard/security/secure-coding-guidelines.md)