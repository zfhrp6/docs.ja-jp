---
title: "Windows フォームで ActiveX コントロールをホストする場合の考慮事項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- ActiveX controls [Windows Forms], hosting
- Windows Forms, ActiveX controls
- Windows Forms, hosting ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 2509302d-a74e-484f-9890-2acdbfa67a68
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 23c8476e4013cca6d906d85f11658deddc585869
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="considerations-when-hosting-an-activex-control-on-a-windows-form"></a><span data-ttu-id="27a54-102">Windows フォームで ActiveX コントロールをホストする場合の考慮事項</span><span class="sxs-lookup"><span data-stu-id="27a54-102">Considerations When Hosting an ActiveX Control on a Windows Form</span></span>
<span data-ttu-id="27a54-103">Windows フォームは、Windows フォーム コントロールをホストするために最適化されていますが、ActiveX コントロールを使うこともできます。</span><span class="sxs-lookup"><span data-stu-id="27a54-103">Although Windows Forms have been optimized to host Windows Forms controls, you can still use ActiveX controls.</span></span> <span data-ttu-id="27a54-104">ActiveX コントロールを使うアプリケーションを計画するときは、次の考慮事項に留意してください。</span><span class="sxs-lookup"><span data-stu-id="27a54-104">Keep the following considerations in mind when planning an application that uses ActiveX controls:</span></span>  
  
-   <span data-ttu-id="27a54-105">**セキュリティ** 共通言語ランタイムは、コード アクセス セキュリティに関して強化されました。</span><span class="sxs-lookup"><span data-stu-id="27a54-105">**Security** The common language runtime has been enhanced with regard to code access security.</span></span> <span data-ttu-id="27a54-106">Windows フォームを使うアプリケーションは、完全に信頼された環境では問題なく動作し、信頼性が高くない環境ではほとんどの機能がアクセス可能な状態で動作します。</span><span class="sxs-lookup"><span data-stu-id="27a54-106">Applications featuring Windows Forms can run in a fully trusted environment without issue and in a semi-trusted environment with most of the functionality accessible.</span></span> <span data-ttu-id="27a54-107">Windows フォーム コントロールは、ブラウザーで問題なくホストできます。</span><span class="sxs-lookup"><span data-stu-id="27a54-107">Windows Forms controls can be hosted in a browser with no complications.</span></span> <span data-ttu-id="27a54-108">ただし、Windows フォームの ActiveX コントロールは、これらのセキュリティ強化を利用できません。</span><span class="sxs-lookup"><span data-stu-id="27a54-108">However, ActiveX controls on Windows Forms cannot take advantage of these security enhancements.</span></span> <span data-ttu-id="27a54-109">ActiveX コントロールの実行で設定されているアンマネージ コードのアクセス許可が必要です、<xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="27a54-109">Running an ActiveX control requires unmanaged code permission, which is set with the <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="27a54-110">セキュリティとアンマネージ コードのアクセス許可の詳細については、次を参照してください。<xref:System.Security.Permissions.SecurityPermissionAttribute>です。</span><span class="sxs-lookup"><span data-stu-id="27a54-110">For more information about security and unmanaged code permission, see <xref:System.Security.Permissions.SecurityPermissionAttribute>.</span></span>  
  
-   <span data-ttu-id="27a54-111">**総保有コスト** Windows フォームに追加される ActiveX コントロールは、その Windows フォーム全体と共に配置されるため、作成されるファイルのサイズが大幅に追加する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="27a54-111">**Total Cost of Ownership** ActiveX controls added to a Windows Form are deployed with that Windows Form in their entirety, which can add significantly to the size of the file(s) created.</span></span> <span data-ttu-id="27a54-112">さらに、Windows フォームで ActiveX コントロールを使うには、レジストリへの書き込みが必要です。</span><span class="sxs-lookup"><span data-stu-id="27a54-112">Additionally, using ActiveX controls on Windows Forms requires writing to the registry.</span></span> <span data-ttu-id="27a54-113">これは、レジストリへの書き込みを必要としない Windows フォーム コントロールと比較して、ユーザーのコンピューターに大きく干渉します。</span><span class="sxs-lookup"><span data-stu-id="27a54-113">This is more invasive to a user's computer than Windows Forms controls, which do not require this.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="27a54-114">ActiveX コントロールを操作するには、COM 相互運用ラッパーを使う必要があります。</span><span class="sxs-lookup"><span data-stu-id="27a54-114">Working with an ActiveX control requires the use of a COM interop wrapper.</span></span> <span data-ttu-id="27a54-115">詳しくは、「[Visual Basic および Visual C# における COM 相互運用性](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="27a54-115">For more information, see [COM Interoperability in Visual Basic and Visual C#](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="27a54-116">ActiveX コントロールのメンバーの名前で定義された名前に一致する場合、 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]、ActiveX コントロール インポーターでメンバー名のプレフィックスは、 **Ctl**を作成すると、<xref:System.Windows.Forms.AxHost>クラスを派生します。</span><span class="sxs-lookup"><span data-stu-id="27a54-116">If the name of a member of the ActiveX control matches a name defined in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], then the ActiveX Control Importer will prefix the member name with **Ctl** when it creates the <xref:System.Windows.Forms.AxHost> derived class.</span></span> <span data-ttu-id="27a54-117">たとえば、ActiveX コントロールに **Layout** という名前のメンバーがある場合、**Layout** イベントが [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 内で定義されているため、AxHost 派生クラスでは **CtlLayout** という名前に変更されます。</span><span class="sxs-lookup"><span data-stu-id="27a54-117">For example, if your ActiveX control has a member named **Layout**, it is renamed **CtlLayout** in the AxHost-derived class because the **Layout** event is defined within the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27a54-118">参照</span><span class="sxs-lookup"><span data-stu-id="27a54-118">See Also</span></span>  
 [<span data-ttu-id="27a54-119">方法: Windows フォームに ActiveX コントロールを追加する</span><span class="sxs-lookup"><span data-stu-id="27a54-119">How to: Add ActiveX Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)  
 [<span data-ttu-id="27a54-120">コード アクセス セキュリティ</span><span class="sxs-lookup"><span data-stu-id="27a54-120">Code Access Security</span></span>](../../../../docs/framework/misc/code-access-security.md)  
 [<span data-ttu-id="27a54-121">各言語およびライブラリにおける、コントロールとプログラミング可能オブジェクトの比較</span><span class="sxs-lookup"><span data-stu-id="27a54-121">Controls and Programmable Objects Compared in Various Languages and Libraries</span></span>](http://msdn.microsoft.com/library/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [<span data-ttu-id="27a54-122">Windows フォームへのコントロールの追加</span><span class="sxs-lookup"><span data-stu-id="27a54-122">Putting Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)  
 [<span data-ttu-id="27a54-123">Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="27a54-123">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)
