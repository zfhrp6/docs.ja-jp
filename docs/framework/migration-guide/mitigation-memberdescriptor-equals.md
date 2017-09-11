---
title: "軽減策: MemberDescriptor.Equals"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf3735f0-0dd4-4bef-b4b0-575264e10f39
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4989d3c2611b500063158955f102931902e1ab32
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-memberdescriptorequals"></a><span data-ttu-id="779d2-102">軽減策: MemberDescriptor.Equals</span><span class="sxs-lookup"><span data-stu-id="779d2-102">Mitigation: MemberDescriptor.Equals</span></span>
<span data-ttu-id="779d2-103">[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降を対象とするアプリでは、<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> メソッドの実装が変更されました。</span><span class="sxs-lookup"><span data-stu-id="779d2-103">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], the implementation of the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> method has changed.</span></span> <span data-ttu-id="779d2-104">`System.ComponentModel.EventDescriptor.Equals` メソッドと `System.ComponentModel.PropertyDescriptor.Equals` メソッドでは基底クラスの実装が継承されるため、変更はこれらのメソッドにも影響します。</span><span class="sxs-lookup"><span data-stu-id="779d2-104">Because the `System.ComponentModel.EventDescriptor.Equals` and  `System.ComponentModel.PropertyDescriptor.Equals` methods inherit the base class implementation, the change also affects these methods.</span></span>  
  
 <span data-ttu-id="779d2-105">.NET Framework [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] より前のバージョンの .NET Framework を対象とするアプリでは、<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> メソッドの一部の等価テストで、あるオブジェクトの <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> プロパティと、別のオブジェクトの <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> プロパティが誤って比較されていました。</span><span class="sxs-lookup"><span data-stu-id="779d2-105">In apps that target versions of the .NET Framework prior to [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a portion of the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> method's test for equality  incorrectly compared the <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> property of one object with the <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> property of the other.</span></span> <span data-ttu-id="779d2-106">[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降を対象とするアプリでは、<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> メソッドで 2 つのオブジェクトの <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> プロパティが比較されます。</span><span class="sxs-lookup"><span data-stu-id="779d2-106">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> method compares the <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> property of the two objects.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="779d2-107">影響</span><span class="sxs-lookup"><span data-stu-id="779d2-107">Impact</span></span>  
 <span data-ttu-id="779d2-108">この変更により、<xref:System.ComponentModel.MemberDescriptor?displayProperty=fullName> オブジェクトの等価テストが正しく実装され、影響は最小限になるはずです。</span><span class="sxs-lookup"><span data-stu-id="779d2-108">This change correctly implements the test for equality for <xref:System.ComponentModel.MemberDescriptor?displayProperty=fullName> objects and should have minimal impact.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="779d2-109">軽減策</span><span class="sxs-lookup"><span data-stu-id="779d2-109">Mitigation</span></span>  
 <span data-ttu-id="779d2-110">[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降のバージョンの .NET Framework を対象とするアプリが、メンバー記述子が等しい場合に `false` を返すことがある <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> メソッドに依存している場合に利用可能な回避策は次の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="779d2-110">Two workarounds are available if your app targets the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or a later version of the .NET Framework and it depends on the  <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> method sometimes returning `false` when member descriptors are equivalent:</span></span>  
  
-   <span data-ttu-id="779d2-111">app.config ファイルの [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに次の行を追加することで、ソース コードを変更せずにこの変更を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="779d2-111">You can opt out of this change without modifying your source code by adding the following to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value = "Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true" />  
     </runtime>  
    ```  
  
-   <span data-ttu-id="779d2-112">次のコード フラグメントのように、ソース コードを変更し、<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> メソッドを呼び出した後で <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> プロパティと <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> プロパティを手動で比較して、以前の動作を復元できます。</span><span class="sxs-lookup"><span data-stu-id="779d2-112">You can modify your source code to restore the previous behavior by manually comparing the  <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> and <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> properties after calling the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> method, as the following code fragment does.</span></span>  
  
    ```csharp  
    if (memberDescriptor1.Equals(memberDescriptor2) &   
        memberDescriptor1.Description.Equals(memberDescriptor2.Category)) {  
          // Code to execute if true.  
    }  
    else {  
          // Code to execute if false.     
    }  
    ```  
  
    ```  
    If memberDescriptor1.Equals(memberDescriptor2) And   
        memberDescriptor1.Description.Equals(memberDescriptor2.Category)  
          // Code to execute if True.  
    Else  
          // Code to execute if False.     
    End If  
    ```  
  
 <span data-ttu-id="779d2-113">[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 以前のバージョンを対象とするアプリでは、app.config ファイルに次の値を追加することで、この変更を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="779d2-113">For apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions, you can enable this change by adding the following value to your app.config file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="779d2-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="779d2-114">See Also</span></span>  
 <span data-ttu-id="779d2-115">[変更の再ターゲット](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md) </span><span class="sxs-lookup"><span data-stu-id="779d2-115">[Retargeting Changes](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md) </span></span>  
 [<span data-ttu-id="779d2-116">4.6.2 でのアプリケーションの互換性</span><span class="sxs-lookup"><span data-stu-id="779d2-116">Application Compatibility in 4.6.2</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)

