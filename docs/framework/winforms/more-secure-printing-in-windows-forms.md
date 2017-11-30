---
title: "Windows フォームでのより安全な印刷"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, printing
- PrintingPermission class [Windows Forms], Windows Forms security
- printing [Windows Forms], security
- security [Windows Forms], printing
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b89a94fd0223d817b0dee37f7a3ed84dcbacbbec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="more-secure-printing-in-windows-forms"></a><span data-ttu-id="aa4b7-102">Windows フォームでのより安全な印刷</span><span class="sxs-lookup"><span data-stu-id="aa4b7-102">More Secure Printing in Windows Forms</span></span>
<span data-ttu-id="aa4b7-103">Windows フォーム アプリケーションには、印刷機能を備えて頻繁に含まれます。</span><span class="sxs-lookup"><span data-stu-id="aa4b7-103">Windows Forms applications frequently include printing abilities.</span></span> <span data-ttu-id="aa4b7-104">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]を使用して、<xref:System.Drawing.Printing.PrintingPermission>クラスからの印刷機能へのアクセス制御および関連付けられた<xref:System.Drawing.Printing.PrintingPermissionLevel>アクセスのレベルを示す列挙値。</span><span class="sxs-lookup"><span data-stu-id="aa4b7-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] uses the <xref:System.Drawing.Printing.PrintingPermission> class to control access to printing capabilities and the associated <xref:System.Drawing.Printing.PrintingPermissionLevel> enumeration value to indicate the level of access.</span></span> <span data-ttu-id="aa4b7-105">既定では、既定では、ローカルのイントラネットとインターネット ゾーンで印刷が有効にします。ただし、アクセスのレベルは、両方の領域で制限されます。</span><span class="sxs-lookup"><span data-stu-id="aa4b7-105">By default, printing is enabled by default in the Local Intranet and Internet zones; however, the level of access is restricted in both zones.</span></span> <span data-ttu-id="aa4b7-106">ユーザーとのやり取りが必要だかどうかを印刷できるアプリケーション、または印刷は、アプリケーションに付与されるアクセス許可の値に依存できません。</span><span class="sxs-lookup"><span data-stu-id="aa4b7-106">Whether your application can print, requires user interaction, or cannot print depends upon the permission value granted to the application.</span></span> <span data-ttu-id="aa4b7-107">ローカル イントラネット ゾーンでは既定では、<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>とイントラネット ゾーンのアクセスを受け取る<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>アクセスします。</span><span class="sxs-lookup"><span data-stu-id="aa4b7-107">By default, the Local Intranet zone receives <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> access and the Intranet zone receives <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> access.</span></span>  
  
 <span data-ttu-id="aa4b7-108">次の表は、各印刷アクセス許可レベルで使用できる機能を示します。</span><span class="sxs-lookup"><span data-stu-id="aa4b7-108">The following table shows the functionality available at each printing permission level.</span></span>  
  
|<span data-ttu-id="aa4b7-109">PrintingPermissionLevel</span><span class="sxs-lookup"><span data-stu-id="aa4b7-109">PrintingPermissionLevel</span></span>|<span data-ttu-id="aa4b7-110">説明</span><span class="sxs-lookup"><span data-stu-id="aa4b7-110">Description</span></span>|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|<span data-ttu-id="aa4b7-111">インストールされているすべてのプリンターへのフル アクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="aa4b7-111">Provides full access to all installed printers.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|<span data-ttu-id="aa4b7-112">既定のプリンターにプログラムによる印刷および制限の厳しい印刷 ダイアログ ボックスを経由した安全な印刷を有効にします。</span><span class="sxs-lookup"><span data-stu-id="aa4b7-112">Enables programmatic printing to the default printer and safer printing through a restrictive printing dialog box.</span></span> <span data-ttu-id="aa4b7-113"><xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> は <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting> のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="aa4b7-113"><xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|<span data-ttu-id="aa4b7-114">制限されたダイアログ ボックスからのみ印刷機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="aa4b7-114">Provides printing only from a more-restricted dialog box.</span></span> <span data-ttu-id="aa4b7-115"><xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> は <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="aa4b7-115"><xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|<span data-ttu-id="aa4b7-116">プリンターにアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="aa4b7-116">Prevents access to printers.</span></span> <span data-ttu-id="aa4b7-117"><xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> は <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="aa4b7-117"><xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aa4b7-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa4b7-118">See Also</span></span>  
 [<span data-ttu-id="aa4b7-119">Windows フォームにおけるファイルおよびデータへのより安全なアクセス</span><span class="sxs-lookup"><span data-stu-id="aa4b7-119">More Secure File and Data Access in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 [<span data-ttu-id="aa4b7-120">Windows フォームのセキュリティに関するその他の考慮事項</span><span class="sxs-lookup"><span data-stu-id="aa4b7-120">Additional Security Considerations in Windows Forms</span></span>](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 [<span data-ttu-id="aa4b7-121">Windows フォームのセキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="aa4b7-121">Security in Windows Forms Overview</span></span>](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [<span data-ttu-id="aa4b7-122">Windows フォームのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="aa4b7-122">Windows Forms Security</span></span>](../../../docs/framework/winforms/windows-forms-security.md)
