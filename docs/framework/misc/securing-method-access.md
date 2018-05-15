---
title: メソッド アクセスの保護
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, method access
- secure coding, method access
- security [.NET Framework], method access
- method access security
ms.assetid: f7c2d6ec-3b18-4e0e-9991-acd97189d818
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b0d9ddbd6c7b027a7c342f4c14192a7571beb592
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="securing-method-access"></a><span data-ttu-id="e963a-102">メソッド アクセスの保護</span><span class="sxs-lookup"><span data-stu-id="e963a-102">Securing Method Access</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="e963a-103">信頼関係のない任意のコードに呼び出しを許可することが不適切なメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="e963a-103">Some methods might not be suitable to allow arbitrary untrusted code to call.</span></span> <span data-ttu-id="e963a-104">このようなメソッドは、制限された情報を提供する、渡された任意の情報を信頼する、パラメーターのエラー チェックを行わない、誤ったパラメーターを受け取って正しく機能しないかなんらかの被害をもたらすなどの、いくつかの危険性をもたらします。</span><span class="sxs-lookup"><span data-stu-id="e963a-104">Such methods pose several risks: The method might provide some restricted information; it might believe any information passed to it; it might not do error checking on the parameters; or with the wrong parameters, it might malfunction or do something harmful.</span></span> <span data-ttu-id="e963a-105">これらのケースを認識し、メソッドを保護するために役立つ措置を講じる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e963a-105">You should be aware of these cases and take action to help protect the method.</span></span>  
  
 <span data-ttu-id="e963a-106">パブリックでの使用を目的としていないメソッドをパブリックとして使用する場合は、メソッドを制限する必要があることがあります。</span><span class="sxs-lookup"><span data-stu-id="e963a-106">In some cases, you might need to restrict methods that are not intended for public use but still must be public.</span></span> <span data-ttu-id="e963a-107">たとえば、独自の DLL 経由で呼び出すインターフェイスはパブリックにする必要があります。しかし、顧客がそのインターフェイスを使用したり、悪意のあるコードがコンポーネントへのエントリ ポイントとして攻略したりするのを防ぐために、そのインターフェイスをパブリックとして公開しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="e963a-107">For example, you might have an interface that needs to be called across your own DLLs and hence must be public, but you do not want to expose it publicly to prevent customers from using it or to prevent malicious code from exploiting the entry point into your component.</span></span> <span data-ttu-id="e963a-108">また、パブリックではあるものの、パブリック使用を想定していないメソッドを制限する一般的な理由として、非常に内部的なインターフェイスで、ドキュメントを残したり、サポートするのを避けたりする場合も考えられます。</span><span class="sxs-lookup"><span data-stu-id="e963a-108">Another common reason to restrict a method not intended for public use (but that must be public) is to avoid having to document and support what might be a very internal interface.</span></span>  
  
 <span data-ttu-id="e963a-109">マネージ コードには、メソッド アクセスを制限するいくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="e963a-109">Managed code offers several ways to restrict method access:</span></span>  
  
-   <span data-ttu-id="e963a-110">クラス、アセンブリ、派生クラスが信頼されている場合は、これらへのアクセシビリティのスコープを制限します。</span><span class="sxs-lookup"><span data-stu-id="e963a-110">Limit the scope of accessibility to the class, assembly, or derived classes, if they can be trusted.</span></span> <span data-ttu-id="e963a-111">これが、メソッド アクセスを制限する最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="e963a-111">This is the simplest way to limit method access.</span></span> <span data-ttu-id="e963a-112">派生クラスが親クラスの ID を共有することがありますが、一般的に、派生クラスは派生元のクラスよりも信頼度が低くなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e963a-112">Note that, in general, derived classes can be less trustworthy than the class they derive from, though in some cases they share the parent class's identity.</span></span> <span data-ttu-id="e963a-113">具体的には、キーワードとの信頼を推測しないでください**保護**、必ずしも使用ではありません、セキュリティ コンテキストでします。</span><span class="sxs-lookup"><span data-stu-id="e963a-113">In particular, do not infer trust from the keyword **protected**, which is not necessarily used in the security context.</span></span>  
  
-   <span data-ttu-id="e963a-114">指定した id 基本的には、特定の呼び出し元だけにメソッド アクセスを制限する[証拠](http://msdn.microsoft.com/library/64ceb7c8-a0b4-46c4-97dc-6c22da0539da)(厳密な名前、発行者、ゾーン、およびなど) を選択します。</span><span class="sxs-lookup"><span data-stu-id="e963a-114">Limit the method access to callers of a specified identity--essentially, any particular [evidence](http://msdn.microsoft.com/library/64ceb7c8-a0b4-46c4-97dc-6c22da0539da) (strong name, publisher, zone, and so on) you choose.</span></span>  
  
-   <span data-ttu-id="e963a-115">選択したアクセス許可を持つ呼び出し元だけにメソッド アクセスを制限します。</span><span class="sxs-lookup"><span data-stu-id="e963a-115">Limit the method access to callers having whatever permissions you select.</span></span>  
  
 <span data-ttu-id="e963a-116">同様に、宣言セキュリティを使用すると、クラスの継承を制御できます。</span><span class="sxs-lookup"><span data-stu-id="e963a-116">Similarly, declarative security allows you to control inheritance of classes.</span></span> <span data-ttu-id="e963a-117">使用することができます**InheritanceDemand**を次を行うには。</span><span class="sxs-lookup"><span data-stu-id="e963a-117">You can use **InheritanceDemand** to do the following:</span></span>  
  
-   <span data-ttu-id="e963a-118">派生したクラスに、特定の ID またはアクセス許可を要求します。</span><span class="sxs-lookup"><span data-stu-id="e963a-118">Require derived classes to have a specified identity or permission.</span></span>  
  
-   <span data-ttu-id="e963a-119">特定のメソッドをオーバーライドする派生クラスに、特定の ID またはアクセス許可を要求します。</span><span class="sxs-lookup"><span data-stu-id="e963a-119">Require derived classes that override specific methods to have a specified identity or permission.</span></span>  
  
 <span data-ttu-id="e963a-120">呼び出し元に特定の厳密な名前による署名を要求することによってアクセスを制限し、パブリック クラスの保護に役立つ方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e963a-120">The following example shows how to help protect a public class for limited access by requiring that callers be signed with a particular strong name.</span></span> <span data-ttu-id="e963a-121">この例では、<xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute>で、**デマンド**厳密な名前です。</span><span class="sxs-lookup"><span data-stu-id="e963a-121">This example uses the <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> with a **Demand** for the strong name.</span></span> <span data-ttu-id="e963a-122">厳密な名前でアセンブリに署名する方法のタスク ベースの詳細については、次を参照してください。[作成と使用](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)です。</span><span class="sxs-lookup"><span data-stu-id="e963a-122">For task-based information on how to sign an assembly with a strong name, see [Creating and Using Strong-Named Assemblies](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
```vb  
<StrongNameIdentityPermissionAttribute(SecurityAction.Demand, PublicKey := "…hex…", Name := "App1", Version := "0.0.0.0")>  _  
Public Class Class1  
End Class  
```  
  
```csharp  
[StrongNameIdentityPermissionAttribute(SecurityAction.Demand, PublicKey="…hex…", Name="App1", Version="0.0.0.0")]  
public class Class1  
{  
  
}   
```  
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a><span data-ttu-id="e963a-123">クラスとメンバーを信頼関係のないコードが使用できないようにする</span><span class="sxs-lookup"><span data-stu-id="e963a-123">Excluding Classes and Members from Use by Untrusted Code</span></span>  
 <span data-ttu-id="e963a-124">このセクションで示す宣言を使用すると、特定のクラスとメソッド、およびプロパティとイベントが部分的な信頼のコードによって使用されるのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="e963a-124">Use the declarations shown in this section to prevent specific classes and methods, as well as properties and events, from being used by partially trusted code.</span></span> <span data-ttu-id="e963a-125">これらの宣言をクラスに適用すると、すべてのメソッド、プロパティ、イベントが保護されますが、フィールドへのアクセスは宣言セキュリティの影響を受けないため、注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="e963a-125">By applying these declarations to a class, you apply the protection to all its methods, properties, and events; however, note that field access is not affected by declarative security.</span></span> <span data-ttu-id="e963a-126">また、リンク確認要求は直前の呼び出し元に対して保護できるようにするだけで、攻撃を受ける可能性が残っています。</span><span class="sxs-lookup"><span data-stu-id="e963a-126">Note also that link demands help protect against only the immediate callers and might still be subject to luring attacks.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e963a-127">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] では、新しい透過性モデルが導入されました。</span><span class="sxs-lookup"><span data-stu-id="e963a-127">A new transparency model has been introduced in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="e963a-128">[透過的セキュリティ コード、レベル 2](../../../docs/framework/misc/security-transparent-code-level-2.md)モデルをセキュリティで保護されたコードを識別、<xref:System.Security.SecurityCriticalAttribute>属性。</span><span class="sxs-lookup"><span data-stu-id="e963a-128">The [Security-Transparent Code, Level 2](../../../docs/framework/misc/security-transparent-code-level-2.md) model identifies secure code with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="e963a-129">セキュリティ クリティカル コードでは、呼び出し元と継承先の両方が完全に信頼されていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="e963a-129">Security-critical code requires both callers and inheritors to be fully trusted.</span></span> <span data-ttu-id="e963a-130">.NET Framework の以前のバージョンのコード アクセス セキュリティ規則で実行されているアセンブリは、レベル 2 のアセンブリを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="e963a-130">Assemblies that are running under the code access security rules from earlier .NET Framework versions can call level 2 assemblies.</span></span> <span data-ttu-id="e963a-131">この場合、セキュリティ クリティカル属性は、完全な信頼のためのリンク確認要求として扱われます。</span><span class="sxs-lookup"><span data-stu-id="e963a-131">In this case, the security-critical attributes will be treated as link demands for full trust.</span></span>  
  
 <span data-ttu-id="e963a-132">アセンブリの厳密な名前で、 [LinkDemand](../../../docs/framework/misc/link-demands.md)はパブリックにアクセスできるメソッド、プロパティ、およびイベントを完全に信頼された呼び出し元にそれらの使用を制限するのにはすべてに適用します。</span><span class="sxs-lookup"><span data-stu-id="e963a-132">In strong-named assemblies, a [LinkDemand](../../../docs/framework/misc/link-demands.md) is applied to all publicly accessible methods, properties, and events therein to restrict their use to fully trusted callers.</span></span> <span data-ttu-id="e963a-133">この機能を無効にするには、<xref:System.Security.AllowPartiallyTrustedCallersAttribute> 属性を適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e963a-133">To disable this feature, you must apply the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="e963a-134">このため、信頼関係のない呼び出し元を除外するクラスを明示的に指定することは、署名のないアセンブリまたはこの属性を持つアセンブリだけに必要です。これらの宣言を使用して、信頼関係のない呼び出し元からの利用を想定していない型のサブセットをマークできます。</span><span class="sxs-lookup"><span data-stu-id="e963a-134">Thus, explicitly marking classes to exclude untrusted callers is necessary only for unsigned assemblies or assemblies with this attribute; you can use these declarations to mark a subset of types therein that are not intended for untrusted callers.</span></span>  
  
 <span data-ttu-id="e963a-135">クラスおよびメンバーを信頼関係のないコードによって使用されるのを防ぐ方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e963a-135">The following examples show how to prevent classes and members from being used by untrusted code.</span></span>  
  
 <span data-ttu-id="e963a-136">パブリックの非シール クラスの場合:</span><span class="sxs-lookup"><span data-stu-id="e963a-136">For public nonsealed classes:</span></span>  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _   
System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
Public Class CanDeriveFromMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public class CanDeriveFromMe  
{  
}  
```  
  
 <span data-ttu-id="e963a-137">パブリックのシール クラスの場合:</span><span class="sxs-lookup"><span data-stu-id="e963a-137">For public sealed classes:</span></span>  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
NotInheritable Public Class CannotDeriveFromMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public sealed class CannotDeriveFromMe  
{  
}  
```  
  
 <span data-ttu-id="e963a-138">パブリックの抽象クラスの場合:</span><span class="sxs-lookup"><span data-stu-id="e963a-138">For public abstract classes:</span></span>  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _  
System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
MustInherit Public Class CannotCreateInstanceOfMe_CanCastToMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public abstract class CannotCreateInstanceOfMe_CanCastToMe{}  
```  
  
 <span data-ttu-id="e963a-139">パブリックの仮想関数の場合:</span><span class="sxs-lookup"><span data-stu-id="e963a-139">For public virtual functions:</span></span>  
  
```vb  
Class Base1   
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Overridable Sub CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe  
End Class 'Base1  
```  
  
```csharp  
class Base1   
{  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
    public virtual void CanOverrideOrCallMe() {}  
}  
```  
  
 <span data-ttu-id="e963a-140">パブリックの抽象関数の場合:</span><span class="sxs-lookup"><span data-stu-id="e963a-140">For public abstract functions:</span></span>  
  
```vb  
MustInherit Class Base2  
    <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Sub MustOverrideMe()  
    End Sub  
End Class 'Base2  
```  
  
```csharp  
abstract class Base2{  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
public abstract void MustOverrideMe();  
}  
```  
  
 <span data-ttu-id="e963a-141">基本クラスが完全な信頼を確認要求しない、パブリック オーバーライド関数の場合:</span><span class="sxs-lookup"><span data-stu-id="e963a-141">For public override functions where the base class does not demand full trust:</span></span>  
  
```vb  
Class Derived  
    Inherits Base1  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.Demand, Name:="FullTrust")> _  
    Public Overrides Sub CanOverrideOrCallMe()  
        MyBase.CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe  
End Class 'Derived  
```  
  
```csharp  
class Derived : Base1  
{     
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.Demand, Name="FullTrust")]      
    public override void CanOverrideOrCallMe()   
    {  
        base.CanOverrideOrCallMe();  
    }  
}  
```  
  
 <span data-ttu-id="e963a-142">基本クラスが完全な信頼を確認要求する、パブリック オーバーライド関数の場合:</span><span class="sxs-lookup"><span data-stu-id="e963a-142">For public override functions where the base class demands full trust:</span></span>  
  
```vb  
Class Derived  
    Inherits Base1  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Overrides Sub CanOverrideOrCallMe()  
        MyBase.CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe   
End Class 'Derived  
```  
  
```csharp  
class Derived : Base1  
{     
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]      
    public override void CanOverrideOrCallMe()   
    {  
        base.CanOverrideOrCallMe();  
    }  
}  
```  
  
 <span data-ttu-id="e963a-143">パブリック インターフェイスの場合:</span><span class="sxs-lookup"><span data-stu-id="e963a-143">For public interfaces:</span></span>  
  
```vb  
Public Interface ICanCastToMe  
    <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust")> _  
    Sub CanImplementMe()  
End Interface 'ICanCastToMe  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust")> _  
Class Implemented  
    Implements ICanCastToMe  
    Public Sub CanImplementMe()  
    End Sub 'CanImplementMe  
```  
  
```csharp  
public interface ICanCastToMe   
{  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
void CanImplementMe();  
}  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
class Implemented : ICanCastToMe  
{  
    public void CanImplementMe()  
    {  
    }  
}  
```  
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a><span data-ttu-id="e963a-144">Virtual Internal Overrides または Overloads Overridable Friend</span><span class="sxs-lookup"><span data-stu-id="e963a-144">Virtual Internal Overrides or Overloads Overridable Friend</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e963a-145">このセクションの内容に関する注意事項について、セキュリティ上の問題両方とメソッドを宣言するときに`virtual`と`internal`(`Overloads``Overridable``Friend` Visual Basic で)。</span><span class="sxs-lookup"><span data-stu-id="e963a-145">This section warns about a security issue when declaring a method as both `virtual` and `internal` (`Overloads``Overridable``Friend` in Visual Basic).</span></span> <span data-ttu-id="e963a-146">この警告は、.NET Framework のバージョン 1.0 および 1.1 にのみ適用されます、以降のバージョンには適用されません。</span><span class="sxs-lookup"><span data-stu-id="e963a-146">This warning applies only to the .NET Framework versions 1.0 and 1.1, it does not apply to later versions.</span></span>  
  
 <span data-ttu-id="e963a-147">.NET Framework バージョン 1.0 および 1.1 では、する必要がありますの型システムのアクセシビリティの微妙な違いに注意してください、コードが他のアセンブリを使用できないことを確認するときにします。</span><span class="sxs-lookup"><span data-stu-id="e963a-147">In the .NET Framework versions 1.0 and 1.1, you must be aware of a nuance of the type system accessibility when confirming that your code is unavailable to other assemblies.</span></span> <span data-ttu-id="e963a-148">宣言されているメソッド**仮想**と**内部**(**Overloads Overridable Friend** Visual Basic で)、親クラスの vtable エントリをオーバーライドすることができますからのみ使用できます同じアセンブリ内で内部になっているためです。</span><span class="sxs-lookup"><span data-stu-id="e963a-148">A method that is declared **virtual** and **internal** (**Overloads Overridable Friend** in Visual Basic) can override the parent class's vtable entry and can be used only from within the same assembly because it is internal.</span></span> <span data-ttu-id="e963a-149">ただし、オーバーライドのアクセシビリティはによって決定、**仮想**キーワード、およびそのコードがクラス自身へのアクセスを持っている限り別のアセンブリからオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="e963a-149">However, the accessibility for overriding is determined by the **virtual** keyword, and this can be overridden from another assembly as long as that code has access to the class itself.</span></span> <span data-ttu-id="e963a-150">オーバーライドの可能性がある問題場合、は、宣言セキュリティを使用して、修正するか、または削除する、**仮想**これは必須ではない場合は、キーワード。</span><span class="sxs-lookup"><span data-stu-id="e963a-150">If the possibility of an override presents a problem, use declarative security to fix it, or remove the **virtual** keyword if it is not strictly required.</span></span>  
  
 <span data-ttu-id="e963a-151">ある言語コンパイラがコンパイル エラーによってこれらのオーバーライドを防いだとしても、他のコンパイラによって記述されたコードがオーバーライドする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e963a-151">Note that even if a language compiler prevents these overrides with a compilation error, it is possible for code written with other compilers to override.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e963a-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="e963a-152">See Also</span></span>  
 [<span data-ttu-id="e963a-153">安全なコーディングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="e963a-153">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
