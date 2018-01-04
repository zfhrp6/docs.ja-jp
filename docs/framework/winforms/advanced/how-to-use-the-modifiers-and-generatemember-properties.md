---
title: "方法 : Modifiers プロパティおよび GenerateMember プロパティを使用する"
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
f1_keywords:
- Designer_GenerateMember
- Designer_Modifiers
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 3381a5e4-e1a3-44e2-a765-a0b758937b85
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f524bab55527bf9d3c744cb6f50d1df1fc9a2302
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-modifiers-and-generatemember-properties"></a><span data-ttu-id="55ee4-102">方法 : Modifiers プロパティおよび GenerateMember プロパティを使用する</span><span class="sxs-lookup"><span data-stu-id="55ee4-102">How to: Use the Modifiers and GenerateMember Properties</span></span>
<span data-ttu-id="55ee4-103">2 つのプロパティが、デザイン環境で提供される Windows フォームでコンポーネントを配置する場合:`GenerateMember`と`Modifiers`です。</span><span class="sxs-lookup"><span data-stu-id="55ee4-103">When you place a component on a Windows Form, two properties are provided by the design environment: `GenerateMember` and `Modifiers`.</span></span> <span data-ttu-id="55ee4-104">`GenerateMember`プロパティは、Windows フォーム デザイナーでコンポーネントのメンバー変数を生成するときを指定します。</span><span class="sxs-lookup"><span data-stu-id="55ee4-104">The `GenerateMember` property specifies when the Windows Forms Designer generates a member variable for a component.</span></span> <span data-ttu-id="55ee4-105">`Modifiers`プロパティは、そのメンバー変数に割り当てられている、アクセス修飾子。</span><span class="sxs-lookup"><span data-stu-id="55ee4-105">The `Modifiers` property is the access modifier assigned to that member variable.</span></span> <span data-ttu-id="55ee4-106">場合の値、`GenerateMember`プロパティは`false`の値、`Modifiers`プロパティは影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="55ee4-106">If the value of the `GenerateMember` property is `false`, the value of the `Modifiers` property has no effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55ee4-107">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="55ee4-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="55ee4-108">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55ee4-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="55ee4-109">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ee4-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-specify-whether-a-component-is-a-member-of-the-form"></a><span data-ttu-id="55ee4-110">コンポーネントからのメンバーであるかどうかを指定するには</span><span class="sxs-lookup"><span data-stu-id="55ee4-110">To specify whether a component is a member of the form</span></span>  
  
1.  <span data-ttu-id="55ee4-111">Windows フォーム デザイナーでフォームを開きます。</span><span class="sxs-lookup"><span data-stu-id="55ee4-111">In the Windows Forms Designer, open your form.</span></span>  
  
2.  <span data-ttu-id="55ee4-112">開く、**ツールボックス**、フォームで、3 つの配置と<xref:System.Windows.Forms.Button>コントロール。</span><span class="sxs-lookup"><span data-stu-id="55ee4-112">Open the **Toolbox**, and on the form, place three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
3.  <span data-ttu-id="55ee4-113">設定、`GenerateMember`と`Modifiers`の各プロパティ<xref:System.Windows.Forms.Button>次の表に従って管理します。</span><span class="sxs-lookup"><span data-stu-id="55ee4-113">Set the `GenerateMember` and `Modifiers` properties for each <xref:System.Windows.Forms.Button> control according to the following table.</span></span>  
  
    |<span data-ttu-id="55ee4-114">ボタン名</span><span class="sxs-lookup"><span data-stu-id="55ee4-114">Button name</span></span>|<span data-ttu-id="55ee4-115">GenerateMember 値</span><span class="sxs-lookup"><span data-stu-id="55ee4-115">GenerateMember value</span></span>|<span data-ttu-id="55ee4-116">修飾子の値</span><span class="sxs-lookup"><span data-stu-id="55ee4-116">Modifiers value</span></span>|  
    |-----------------|--------------------------|---------------------|  
    |`button1`|`true`|`private`|  
    |`button2`|`true`|`protected`|  
    |`button3`|`false`|<span data-ttu-id="55ee4-117">変更はありません。</span><span class="sxs-lookup"><span data-stu-id="55ee4-117">No change</span></span>|  
  
4.  <span data-ttu-id="55ee4-118">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="55ee4-118">Build the solution.</span></span>  
  
5.  <span data-ttu-id="55ee4-119">**ソリューション エクスプローラー**で、**[すべてのファイルを表示]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="55ee4-119">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
6.  <span data-ttu-id="55ee4-120">開く、 **Form1**ノード、および、**コード エディター**、開かれている、 **Form1.Designer.vb**または**Form1.Designer.cs**ファイル。</span><span class="sxs-lookup"><span data-stu-id="55ee4-120">Open the **Form1** node, and in the **Code Editor**,open the **Form1.Designer.vb** or **Form1.Designer.cs** file.</span></span> <span data-ttu-id="55ee4-121">このファイルには、Windows フォーム デザイナーによって生成されます。 コードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="55ee4-121">This file contains the code emitted by the Windows Forms Designer.</span></span>  
  
7.  <span data-ttu-id="55ee4-122">3 つのボタンの宣言を検索します。</span><span class="sxs-lookup"><span data-stu-id="55ee4-122">Find the declarations for the three buttons.</span></span> <span data-ttu-id="55ee4-123">次のコード例で指定されたの違いを示します、`GenerateMember`と`Modifiers`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="55ee4-123">The following code example shows the differences specified by the `GenerateMember` and `Modifiers` properties.</span></span>  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#2)]  
  
> [!NOTE]
>  <span data-ttu-id="55ee4-124">既定では、Windows フォーム デザイナーが割り当てられます、 `private` (`Friend` Visual basic) 修飾子などのコンテナー コントロールを<xref:System.Windows.Forms.Panel>です。</span><span class="sxs-lookup"><span data-stu-id="55ee4-124">By default, the Windows Forms Designer assigns the `private` (`Friend` in Visual Basic) modifier to container controls like <xref:System.Windows.Forms.Panel>.</span></span> <span data-ttu-id="55ee4-125">場合、ベース<xref:System.Windows.Forms.UserControl>または<xref:System.Windows.Forms.Form>コンテナー コントロールを持つ継承されたコントロールとフォームで新しい子を入力することはできません。</span><span class="sxs-lookup"><span data-stu-id="55ee4-125">If your base <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Form> has a container control, it will not accept new children in inherited controls and forms.</span></span> <span data-ttu-id="55ee4-126">解決する基本のコンテナー コントロールの修飾子を変更するには`protected`または`public`です。</span><span class="sxs-lookup"><span data-stu-id="55ee4-126">The solution is to change the modifier of the base container control to `protected` or `public`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55ee4-127">参照</span><span class="sxs-lookup"><span data-stu-id="55ee4-127">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="55ee4-128">Windows フォームのビジュアルの継承</span><span class="sxs-lookup"><span data-stu-id="55ee4-128">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [<span data-ttu-id="55ee4-129">チュートリアル: ビジュアル継承のデモンストレーション</span><span class="sxs-lookup"><span data-stu-id="55ee4-129">Walkthrough: Demonstrating Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-demonstrating-visual-inheritance.md)  
 [<span data-ttu-id="55ee4-130">方法: Windows フォームを継承する</span><span class="sxs-lookup"><span data-stu-id="55ee4-130">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)
