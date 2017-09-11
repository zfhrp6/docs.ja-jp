---
title: "方法: ActiveX コントロール (Visual Basic) の使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Toolbox, adding controls
- ActiveX controls, adding to Toolbox
ms.assetid: ec675027-866f-4c05-aaf2-92fca5200f9a
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0ae1e5158ad83a6a7d45fa7820a707dbca1af3f3
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-work-with-activex-controls-visual-basic"></a><span data-ttu-id="d47aa-102">方法: ActiveX コントロールを操作する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d47aa-102">How to: Work with ActiveX Controls (Visual Basic)</span></span>
<span data-ttu-id="d47aa-103">ActiveX コントロールは、COM コンポーネントまたは Web ページやプログラムには、他のユーザー パッケージの機能を再利用するには、他のアプリケーションに挿入できるオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="d47aa-103">ActiveX controls are COM components or objects you can insert into a Web page or other application to reuse packaged functionality someone else has programmed.</span></span> <span data-ttu-id="d47aa-104">Visual Basic 6.0 とそれ以前のバージョン用に開発された ActiveX コントロールを使用するには機能を追加する、**ツールボックス**の[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="d47aa-104">You can use ActiveX controls developed for Visual Basic 6.0 and earlier versions to add features to the **Toolbox** of [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)].</span></span>  
  
### <a name="to-add-activex-controls-to-the-toolbox"></a><span data-ttu-id="d47aa-105">ActiveX コントロールをツールボックスに追加するには</span><span class="sxs-lookup"><span data-stu-id="d47aa-105">To add ActiveX controls to the toolbox</span></span>  
  
1.  <span data-ttu-id="d47aa-106">**ツール**] メニューのをクリックして**[ツールボックス アイテムの**です。</span><span class="sxs-lookup"><span data-stu-id="d47aa-106">On the **Tools** menu, click **Choose Toolbox Items**.</span></span>  
  
     <span data-ttu-id="d47aa-107">**ツールボックス アイテムの選択** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d47aa-107">The **Choose Toolbox** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="d47aa-108">クリックして、 **COM コンポーネント** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d47aa-108">Click the **COM Components** tab.</span></span>  
  
3.  <span data-ttu-id="d47aa-109">クリックして、使用する ActiveX コントロールの横にあるチェック ボックスをオンに**OK**します。</span><span class="sxs-lookup"><span data-stu-id="d47aa-109">Select the check box next to the ActiveX control you want to use, and then click **OK**.</span></span>  
  
     <span data-ttu-id="d47aa-110">その他のツールを使用してこの新しいコントロールが表示されます、**ツールボックス**します。</span><span class="sxs-lookup"><span data-stu-id="d47aa-110">The new control appears with the other tools in the **Toolbox**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d47aa-111">Aximp ユーティリティを使用して、ActiveX コントロールの相互運用機能アセンブリを手動で作成することができます。</span><span class="sxs-lookup"><span data-stu-id="d47aa-111">You can use the Aximp utility to manually create an interop assembly for ActiveX controls.</span></span> <span data-ttu-id="d47aa-112">詳細については、次を参照してください。 [Aximp.exe (Windows フォーム ActiveX コントロール インポーター)](http://msdn.microsoft.com/library/482c0d83-7144-4497-b626-87d2351b78d0)します。</span><span class="sxs-lookup"><span data-stu-id="d47aa-112">For more information, see [Aximp.exe (Windows Forms ActiveX Control Importer)](http://msdn.microsoft.com/library/482c0d83-7144-4497-b626-87d2351b78d0).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d47aa-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="d47aa-113">See Also</span></span>  
 <span data-ttu-id="d47aa-114">[COM 相互運用機能](../../../visual-basic/programming-guide/com-interop/index.md) </span><span class="sxs-lookup"><span data-stu-id="d47aa-114">[COM Interop](../../../visual-basic/programming-guide/com-interop/index.md) </span></span>  
<span data-ttu-id="d47aa-115"> [方法: Windows フォームに ActiveX コントロールを追加します。](http://msdn.microsoft.com/library/54a61e5b-555e-4887-b41e-6244fed271eb) </span><span class="sxs-lookup"><span data-stu-id="d47aa-115"> [How to: Add ActiveX Controls to Windows Forms](http://msdn.microsoft.com/library/54a61e5b-555e-4887-b41e-6244fed271eb) </span></span>  
<span data-ttu-id="d47aa-116"> [Aximp.exe (Windows フォーム ActiveX コントロール インポーター)](http://msdn.microsoft.com/library/482c0d83-7144-4497-b626-87d2351b78d0) </span><span class="sxs-lookup"><span data-stu-id="d47aa-116"> [Aximp.exe (Windows Forms ActiveX Control Importer)](http://msdn.microsoft.com/library/482c0d83-7144-4497-b626-87d2351b78d0) </span></span>  
<span data-ttu-id="d47aa-117"> [Windows フォームで ActiveX コントロールをホストする際の考慮事項](http://msdn.microsoft.com/library/2509302d-a74e-484f-9890-2acdbfa67a68) </span><span class="sxs-lookup"><span data-stu-id="d47aa-117"> [Considerations When Hosting an ActiveX Control on a Windows Form](http://msdn.microsoft.com/library/2509302d-a74e-484f-9890-2acdbfa67a68) </span></span>  
<span data-ttu-id="d47aa-118"> [相互運用性のトラブルシューティング](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)</span><span class="sxs-lookup"><span data-stu-id="d47aa-118"> [Troubleshooting Interoperability](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)</span></span>
