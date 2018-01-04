---
title: "方法 : コントロールにツールボックス ビットマップを指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 947ac4f8783b388135cf9e8147bb48eda93cfa08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a><span data-ttu-id="d7900-102">方法 : コントロールにツールボックス ビットマップを指定する</span><span class="sxs-lookup"><span data-stu-id="d7900-102">How to: Provide a Toolbox Bitmap for a Control</span></span>
<span data-ttu-id="d7900-103">コントロールの特別なアイコンが表示する場合、**ツールボックス**を使用して特定のイメージを指定することができます、<xref:System.Drawing.ToolboxBitmapAttribute>です。</span><span class="sxs-lookup"><span data-stu-id="d7900-103">If you want to have a special icon for your control appear in the **Toolbox**, you can specify a particular image by using the <xref:System.Drawing.ToolboxBitmapAttribute>.</span></span> <span data-ttu-id="d7900-104">このクラスは "*属性*" であり、他のクラスに追加できる特殊なクラスです。</span><span class="sxs-lookup"><span data-stu-id="d7900-104">This class is an *attribute*, a special kind of class you can attach to other classes.</span></span> <span data-ttu-id="d7900-105">属性の詳細については、[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] の場合は [Visual Basic での属性の概要](http://msdn.microsoft.com/en-us/0d0cff64-892d-4f57-83bd-bef388553d4f)に関するページを、[!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] の場合は[属性](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7900-105">For more information about attributes, see [NOT IN BUILD: Attributes Overview in Visual Basic](http://msdn.microsoft.com/en-us/0d0cff64-892d-4f57-83bd-bef388553d4f) for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] and [Attributes](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205) for [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].</span></span>  
  
 <span data-ttu-id="d7900-106">使用して、 <xref:System.Drawing.ToolboxBitmapAttribute>16 で 16 ピクセルのビットマップのパスとファイル名を示す文字列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d7900-106">Using the <xref:System.Drawing.ToolboxBitmapAttribute>, you can specify a string that indicates the path and file name for a 16 by 16 pixel bitmap.</span></span> <span data-ttu-id="d7900-107">コントロールを**ツールボックス**に追加すると、このビットマップがコントロールの横に表示されます。</span><span class="sxs-lookup"><span data-stu-id="d7900-107">This bitmap then appears next to your control when added to the **Toolbox**.</span></span> <span data-ttu-id="d7900-108">指定することも、 <xref:System.Type>、その種類に関連付けられたビットマップが読み込まれている場合。</span><span class="sxs-lookup"><span data-stu-id="d7900-108">You can also specify a <xref:System.Type>, in which case the bitmap associated with that type is loaded.</span></span> <span data-ttu-id="d7900-109">両方を指定する場合、<xref:System.Type>文字列、コントロールを検索対象のイメージ リソースで指定された型を含むアセンブリの文字列パラメーターで指定された名前を持つ、<xref:System.Type>パラメーター。</span><span class="sxs-lookup"><span data-stu-id="d7900-109">If you specify both a <xref:System.Type> and a string, the control searches for an image resource with the name specified by the string parameter in the assembly containing the type specified by the <xref:System.Type> parameter.</span></span>  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a><span data-ttu-id="d7900-110">コントロールのツールボックス ビットマップを指定するには</span><span class="sxs-lookup"><span data-stu-id="d7900-110">To specify a Toolbox bitmap for your control</span></span>  
  
1.  <span data-ttu-id="d7900-111">追加、<xref:System.Drawing.ToolboxBitmapAttribute>する前に、コントロールのクラス宣言に、`Class`のキーワード[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]、以降のクラス宣言[!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="d7900-111">Add the <xref:System.Drawing.ToolboxBitmapAttribute> to the class declaration of your control before the `Class` keyword for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], and above the class declaration for [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].</span></span>  
  
    ```vb  
    ' Specifies the bitmap associated with the Button type.  
    <ToolboxBitmap(GetType(Button))> Class MyControl1  
    ' Specifies a bitmap file.  
    End Class  
    <ToolboxBitmap("C:\Documents and Settings\Joe\MyPics\myImage.bmp")> _  
       Class MyControl2  
    End Class  
    ' Specifies a type that indicates the assembly to search, and the name   
    ' of an image resource to look for.  
    <ToolboxBitmap(GetType(MyControl), "MyControlBitmap")> Class MyControl  
    End Class  
    ```  
  
    ```csharp  
    // Specifies the bitmap associated with the Button type.  
    [ToolboxBitmap(typeof(Button))]  
    class MyControl1 : UserControl  
    {  
    }  
    // Specifies a bitmap file.  
    [ToolboxBitmap(@"C:\Documents and Settings\Joe\MyPics\myImage.bmp")]  
    class MyControl2 : UserControl  
    {  
    }  
    // Specifies a type that indicates the assembly to search, and the name   
    // of an image resource to look for.  
    [ToolboxBitmap(typeof(MyControl), "MyControlBitmap")]  
    class MyControl : UserControl  
    {  
    }  
    ```  
  
2.  <span data-ttu-id="d7900-112">プロジェクトをリビルドします。</span><span class="sxs-lookup"><span data-stu-id="d7900-112">Rebuild the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d7900-113">ビットマップは、自動生成されたコントロールとコンポーネントのツールボックスには表示されません。</span><span class="sxs-lookup"><span data-stu-id="d7900-113">The bitmap does not appear in the Toolbox for autogenerated controls and components.</span></span> <span data-ttu-id="d7900-114">ビットマップを表示するには、**[ツールボックス アイテムの選択]** ダイアログ ボックスを使用してコントロールを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="d7900-114">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="d7900-115">詳細については、「[チュートリアル: ツールボックスへのカスタム コンポーネントの自動設定](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7900-115">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7900-116">参照</span><span class="sxs-lookup"><span data-stu-id="d7900-116">See Also</span></span>  
 <xref:System.Drawing.ToolboxBitmapAttribute>  
 [<span data-ttu-id="d7900-117">チュートリアル: ツールボックスへのカスタム コンポーネントの自動設定</span><span class="sxs-lookup"><span data-stu-id="d7900-117">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 [<span data-ttu-id="d7900-118">デザイン時の Windows フォーム コントロールの開発</span><span class="sxs-lookup"><span data-stu-id="d7900-118">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="d7900-119">属性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7900-119">Attributes (Visual Basic)</span></span>](~/docs/visual-basic/language-reference/attributes.md)  
 [<span data-ttu-id="d7900-120">属性</span><span class="sxs-lookup"><span data-stu-id="d7900-120">Attributes</span></span>](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
