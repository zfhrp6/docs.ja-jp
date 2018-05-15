---
title: Windows フォームのビジュアルの継承
ms.date: 03/30/2017
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inheritance
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 857eb737-3602-4d49-bd8b-f70d33ace345
ms.openlocfilehash: 6cf2a7d95f7f6b015c785859b646a5d42f907127
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="windows-forms-visual-inheritance"></a><span data-ttu-id="9b7e1-102">Windows フォームのビジュアルの継承</span><span class="sxs-lookup"><span data-stu-id="9b7e1-102">Windows Forms Visual Inheritance</span></span>
<span data-ttu-id="9b7e1-103">プロジェクトで、以前のプロジェクトで作成したフォームと類似するフォームが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9b7e1-103">Occasionally, you may decide that a project calls for a form similar to one that you have created in a previous project.</span></span> <span data-ttu-id="9b7e1-104">また、プロジェクトで再利用する透かしやコントロールの特定のレイアウトなどが設定された基本フォームを作成し、元のフォーム テンプレートに変更を加えながら繰り返し使用することが必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="9b7e1-104">Or, you may want to create a basic form with settings such as a watermark or certain control layout that you will then use again within a project, with each iteration containing modifications to the original form template.</span></span> <span data-ttu-id="9b7e1-105">フォームの継承を使用すると、基本フォームを作成してそのフォームを継承し、必要な元の設定を保持しながら変更を加えることができます。</span><span class="sxs-lookup"><span data-stu-id="9b7e1-105">Form inheritance enables you to create a base form and then inherit from it and make modifications while preserving whatever original settings you need.</span></span>  
  
 <span data-ttu-id="9b7e1-106">派生クラスのフォームは、プログラムで作成することも、ビジュアル継承ピッカーを使用して作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="9b7e1-106">You can create derived-class forms programmatically or by using the Visual Inheritance picker.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b7e1-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9b7e1-107">In This Section</span></span>  
 [<span data-ttu-id="9b7e1-108">方法 : Windows フォームを継承する</span><span class="sxs-lookup"><span data-stu-id="9b7e1-108">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 <span data-ttu-id="9b7e1-109">継承されたフォームをコードで作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b7e1-109">Gives directions for creating inherited forms in code.</span></span>  
  
 <span data-ttu-id="9b7e1-110">[方法 : [継承ピッカー] ダイアログ ボックスを使用してフォームを継承する](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="9b7e1-110">[How to: Inherit Forms Using the Inheritance Picker Dialog Box](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)</span></span>  
 <span data-ttu-id="9b7e1-111">継承ピッカーを使用して継承されたフォームを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b7e1-111">Gives directions for creating inherited forms with the Inheritance Picker.</span></span>  
  
 [<span data-ttu-id="9b7e1-112">基本フォームの外観を変更した場合の影響</span><span class="sxs-lookup"><span data-stu-id="9b7e1-112">Effects of Modifying a Base Form's Appearance</span></span>](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 <span data-ttu-id="9b7e1-113">基本フォームのコントロールとそのプロパティを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b7e1-113">Gives directions for changing a base form's controls and their properties.</span></span>  
  
 [<span data-ttu-id="9b7e1-114">チュートリアル : ビジュアル継承のデモンストレーション</span><span class="sxs-lookup"><span data-stu-id="9b7e1-114">Walkthrough: Demonstrating Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-demonstrating-visual-inheritance.md)  
 <span data-ttu-id="9b7e1-115">基本的な Windows フォームを作成し、クラス ライブラリにコンパイルする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b7e1-115">Describes how to create a base Windows Form and compile it into a class library.</span></span> <span data-ttu-id="9b7e1-116">このクラス ライブラリを別のプロジェクトにインポートし、基本フォームから継承した新しいフォームを作成します。</span><span class="sxs-lookup"><span data-stu-id="9b7e1-116">You will import this class library into another project, and create a new form that inherits from the base form.</span></span>  
  
 [<span data-ttu-id="9b7e1-117">方法 : Modifiers プロパティおよび GenerateMember プロパティを使用する</span><span class="sxs-lookup"><span data-stu-id="9b7e1-117">How to: Use the Modifiers and GenerateMember Properties</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-the-modifiers-and-generatemember-properties.md)  
 <span data-ttu-id="9b7e1-118">`GenerateMember` プロパティと `Modifiers` プロパティの使用方法について説明します。これらのプロパティは、Windows フォーム デザイナーでコンポーネントのメンバー変数を生成するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="9b7e1-118">Gives directions for using the `GenerateMember` and `Modifiers` properties, which are relevant when the Windows Forms Designer generates a member variable for a component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9b7e1-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b7e1-119">Related Sections</span></span>  
 [<span data-ttu-id="9b7e1-120">継承の基礎 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b7e1-120">Inheritance basics (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 <span data-ttu-id="9b7e1-121">他のクラスの基本クラスとして機能する Visual Basic クラスを定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b7e1-121">Describes how to define Visual Basic classes that serve as the basis for other classes.</span></span>  
  
 [<span data-ttu-id="9b7e1-122">class</span><span class="sxs-lookup"><span data-stu-id="9b7e1-122">class</span></span>](~/docs/csharp/language-reference/keywords/class.md)  
 <span data-ttu-id="9b7e1-123">C# で許可されるクラスの単一継承について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b7e1-123">Describes the C# approach of classes, in which single inheritance is allowed.</span></span>  
  
 [<span data-ttu-id="9b7e1-124">Visual Basic での継承されたイベント ハンドラーのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="9b7e1-124">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="9b7e1-125">継承されたコンポーネントのイベント ハンドラーで発生する一般的な問題を示します。</span><span class="sxs-lookup"><span data-stu-id="9b7e1-125">Lists common issues that arise with event handlers in inherited components</span></span>
