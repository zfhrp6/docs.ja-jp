---
title: "チュートリアル : ユーザー補助対応の Windows ベースのアプリケーションの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8f0a35b569b38e0d7ca79129f720034420ecd23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a><span data-ttu-id="4a533-102">チュートリアル : ユーザー補助対応の Windows ベースのアプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="4a533-102">Walkthrough: Creating an Accessible Windows-based Application</span></span>
<span data-ttu-id="4a533-103">ユーザー補助に対応するアプリケーションを作成することは、ビジネスに重要な影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="4a533-103">Creating an accessible application has important business implications.</span></span> <span data-ttu-id="4a533-104">多くの政府は、ソフトウェアの購入に関するユーザー補助の規制があります。</span><span class="sxs-lookup"><span data-stu-id="4a533-104">Many governments have accessibility regulations for software purchase.</span></span> <span data-ttu-id="4a533-105">Certified for Windows ロゴには、ユーザー補助に関する要件が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4a533-105">The Certified for Windows logo includes accessibility requirements.</span></span> <span data-ttu-id="4a533-106">米国だけでも 3000 万人 (その多くは潜在的な顧客) が、ソフトウェアのアクセシビリティ機能によって影響を受けると推定されています。</span><span class="sxs-lookup"><span data-stu-id="4a533-106">An estimated 30 million residents of the U.S. alone, many of them potential customers, are affected by the accessibility of software.</span></span>  
  
 <span data-ttu-id="4a533-107">このチュートリアルにより、Certified for Windows ロゴの 5 つのユーザー補助機能の要件に対応します。</span><span class="sxs-lookup"><span data-stu-id="4a533-107">This walkthrough will address the five accessibility requirements for the Certified for Windows logo.</span></span> <span data-ttu-id="4a533-108">これらの要件によると、ユーザー補助機能を持つアプリケーションとは、次のようなアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="4a533-108">According to these requirements, an accessible application will:</span></span>  
  
-   <span data-ttu-id="4a533-109">コントロール パネルのサイズ、色、フォント、および入力設定をサポートします。</span><span class="sxs-lookup"><span data-stu-id="4a533-109">Support Control Panel size, color, font, and input settings.</span></span> <span data-ttu-id="4a533-110">ユーザーがコントロール パネルの設定を変更すると、メニュー バー、タイトル バー、罫線、およびステータス バーはすべてサイズが変更されます。</span><span class="sxs-lookup"><span data-stu-id="4a533-110">The menu bar, title bar, borders, and status bar will all resize themselves when the user changes the control panel settings.</span></span> <span data-ttu-id="4a533-111">このアプリケーションでは、コントロールまたはコードに追加の変更は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="4a533-111">No additional changes to the controls or code are required in this application.</span></span>  
  
-   <span data-ttu-id="4a533-112">ハイ コントラスト モードをサポートします。</span><span class="sxs-lookup"><span data-stu-id="4a533-112">Support High Contrast mode.</span></span>  
  
-   <span data-ttu-id="4a533-113">すべての機能に対して文書化されたキーボード アクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="4a533-113">Provide documented keyboard access to all features.</span></span>  
  
-   <span data-ttu-id="4a533-114">キーボード フォーカスの場所を視覚的およびプログラムで公開します。</span><span class="sxs-lookup"><span data-stu-id="4a533-114">Expose location of the keyboard focus visually and programmatically.</span></span>  
  
-   <span data-ttu-id="4a533-115">サウンドだけで重要な情報を伝達しないようにします。</span><span class="sxs-lookup"><span data-stu-id="4a533-115">Avoid conveying important information by sound alone.</span></span>  
  
 <span data-ttu-id="4a533-116">詳細については、「[ユーザー補助アプリケーションのデザイン リソース](/visualstudio/ide/reference/resources-for-designing-accessible-applications)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a533-116">For more information, see [Resources for Designing Accessible Applications](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span></span>  
  
 <span data-ttu-id="4a533-117">さまざまなキーボード レイアウトをサポートする方法については、「[推奨される国際対応アプリケーション開発手順](../../../../docs/standard/globalization-localization/best-practices-for-developing-world-ready-apps.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a533-117">For information on supporting varying keyboard layouts, see [Best Practices for Developing World-Ready Applications](../../../../docs/standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="4a533-118">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="4a533-118">Creating the Project</span></span>  
 <span data-ttu-id="4a533-119">このチュートリアルでは、ピザの注文を受け取るためのアプリケーションのユーザー インターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4a533-119">This walkthrough creates the user interface for an application that takes pizza orders.</span></span> <span data-ttu-id="4a533-120">顧客の名前のための <xref:System.Windows.Forms.TextBox>、ピザのサイズを選択する <xref:System.Windows.Forms.RadioButton> グループ、トッピングを選択するための <xref:System.Windows.Forms.CheckedListBox>、[注文] と [キャンセル] のラベルの付いた 2 つのボタン コントロール、および [終了] コマンドのあるメニューで構成されます。</span><span class="sxs-lookup"><span data-stu-id="4a533-120">It consists of a <xref:System.Windows.Forms.TextBox> for the customer's name, a <xref:System.Windows.Forms.RadioButton> group to select the pizza size, a <xref:System.Windows.Forms.CheckedListBox> for selecting the toppings, two Button controls labeled Order and Cancel, and a Menu with an Exit command.</span></span>  
  
 <span data-ttu-id="4a533-121">ユーザーが、顧客の名前、ピザのサイズ、および希望のトッピングを入力します。</span><span class="sxs-lookup"><span data-stu-id="4a533-121">The user enters the customer's name, the size of the pizza, and the toppings desired.</span></span> <span data-ttu-id="4a533-122">ユーザーが [注文] ボタンをクリックすると、メッセージ ボックスに注文の概要と値段が表示され、コントロールがクリアされて次の注文のために準備します。</span><span class="sxs-lookup"><span data-stu-id="4a533-122">When the user clicks the Order button, a summary of the order and its cost are displayed in a message box and the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="4a533-123">ユーザーが [キャンセル] ボタンをクリックすると、コントロールがクリアされて、次の注文のための準備ができた状態になります。</span><span class="sxs-lookup"><span data-stu-id="4a533-123">When the user clicks the Cancel button, the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="4a533-124">ユーザーが [終了] メニュー項目をクリックすると、プログラムを閉じます。</span><span class="sxs-lookup"><span data-stu-id="4a533-124">When the user clicks the Exit menu item, the program closes.</span></span>  
  
 <span data-ttu-id="4a533-125">このチュートリアルの重点は、販売注文システムのコードではなく、ユーザー インターフェイスのユーザー補助機能です。</span><span class="sxs-lookup"><span data-stu-id="4a533-125">The emphasis of this walkthrough is not the code for a retail order system, but the accessibility of the user interface.</span></span> <span data-ttu-id="4a533-126">このチュートリアルは、ボタン、オプション ボタン、テキスト ボックス、およびラベルなど、頻繁に使用されるいくつかのコントロールのユーザー補助機能を示します。</span><span class="sxs-lookup"><span data-stu-id="4a533-126">The walkthrough demonstrates the accessibility features of several frequently used controls, including buttons, radio buttons, text boxes, and labels.</span></span>  
  
#### <a name="to-begin-making-the-application"></a><span data-ttu-id="4a533-127">アプリケーションの作成を開始するには</span><span class="sxs-lookup"><span data-stu-id="4a533-127">To begin making the application</span></span>  
  
-   <span data-ttu-id="4a533-128">[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] で新しい Windows アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="4a533-128">Create a new Windows Application in [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].</span></span> <span data-ttu-id="4a533-129">プロジェクトに **PizzaOrder** という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="4a533-129">Name the project **PizzaOrder**.</span></span> <span data-ttu-id="4a533-130">(詳細については、「[ソリューションとプロジェクトの作成](/visualstudio/ide/creating-solutions-and-projects)」を参照。)</span><span class="sxs-lookup"><span data-stu-id="4a533-130">(For details see [Creating New Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).)</span></span>  
  
## <a name="adding-the-controls-to-the-form"></a><span data-ttu-id="4a533-131">フォームへのコントロールの追加</span><span class="sxs-lookup"><span data-stu-id="4a533-131">Adding the Controls to the Form</span></span>  
 <span data-ttu-id="4a533-132">フォームにコントロールを追加するときは、ユーザー補助に対応したアプリケーション作成のガイドラインに従うよう注意してください。</span><span class="sxs-lookup"><span data-stu-id="4a533-132">When adding the controls to a form, keep in mind the following guidelines to make an accessible application:</span></span>  
  
-   <span data-ttu-id="4a533-133"><xref:System.Windows.Forms.Control.AccessibleDescription%2A> プロパティと <xref:System.Windows.Forms.Control.AccessibleName%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="4a533-133">Set the <xref:System.Windows.Forms.Control.AccessibleDescription%2A> and <xref:System.Windows.Forms.Control.AccessibleName%2A> properties.</span></span> <span data-ttu-id="4a533-134">この例では、<xref:System.Windows.Forms.Control.AccessibleRole%2A> の既定の設定で十分です。</span><span class="sxs-lookup"><span data-stu-id="4a533-134">In this example, the Default setting for the <xref:System.Windows.Forms.Control.AccessibleRole%2A> is sufficient.</span></span> <span data-ttu-id="4a533-135">アクセシビリティのプロパティの詳細については「[Windows フォーム上のコントロールのユーザー補助情報の提供](../../../../docs/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a533-135">For more information on the accessibility properties, see [Providing Accessibility Information for Controls on a Windows Form](../../../../docs/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span></span>  
  
-   <span data-ttu-id="4a533-136">フォント サイズを 10 ポイント以上に設定します。</span><span class="sxs-lookup"><span data-stu-id="4a533-136">Set the font size to 10 points or larger.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4a533-137">開始するときに、フォームのフォント サイズを 10 に設定すると、その後フォームに追加されるすべてのコントロールのフォント サイズが 10 になります。</span><span class="sxs-lookup"><span data-stu-id="4a533-137">If you set the font size of the form to 10 when you start, then all controls subsequently added to the form will have a font size of 10.</span></span>  
  
-   <span data-ttu-id="4a533-138">TextBox コントロールを説明するラベル コントロールが、タブ オーダーで TextBox コントロールのすぐ前になるようにします。</span><span class="sxs-lookup"><span data-stu-id="4a533-138">Make sure any Label control that describes a TextBox control immediately precedes the TextBox control in the tab order.</span></span>  
  
-   <span data-ttu-id="4a533-139">"&"の文字を使用して、ユーザーが移動する先のコントロールの <xref:System.Windows.Forms.Control.Text%2A> プロパティにアクセス キーを追加します。</span><span class="sxs-lookup"><span data-stu-id="4a533-139">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of any control the user may want to navigate to.</span></span>  
  
-   <span data-ttu-id="4a533-140">"&"の文字を使用して、ユーザーが移動する先のコントロールに先行するラベルの <xref:System.Windows.Forms.Control.Text%2A> プロパティにアクセス キーを追加します。</span><span class="sxs-lookup"><span data-stu-id="4a533-140">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of the label that precedes a control that the user may want to navigate to.</span></span> <span data-ttu-id="4a533-141">ラベルの <xref:System.Windows.Forms.Label.UseMnemonic%2A> プロパティを `true` に設定し、ユーザーがアクセス キーを押したときに、フォーカスがタブ オーダーで次のコントロールに設定されるようにします。</span><span class="sxs-lookup"><span data-stu-id="4a533-141">Set the labels' <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`, so that the focus is set to the next control in the tab order when the user presses the access key.</span></span>  
  
-   <span data-ttu-id="4a533-142">アクセス キーをすべてのメニュー項目に追加します。</span><span class="sxs-lookup"><span data-stu-id="4a533-142">Add access keys to all menu items.</span></span>  
  
#### <a name="to-make-your-windows-application-accessible"></a><span data-ttu-id="4a533-143">Windows アプリケーションをユーザー補助に対応させるには</span><span class="sxs-lookup"><span data-stu-id="4a533-143">To make your Windows Application accessible</span></span>  
  
-   <span data-ttu-id="4a533-144">フォームにコントロールを追加し、以下に示すように、プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="4a533-144">Add the controls to the form and set the properties as described below.</span></span> <span data-ttu-id="4a533-145">フォームにコントロールを配置する方法のモデルについては、表の最後の画像を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a533-145">See the picture at the end of the table for a model of how to arrange the controls on the form.</span></span>  
  
    |<span data-ttu-id="4a533-146">オブジェクト</span><span class="sxs-lookup"><span data-stu-id="4a533-146">Object</span></span>|<span data-ttu-id="4a533-147">プロパティ</span><span class="sxs-lookup"><span data-stu-id="4a533-147">Property</span></span>|<span data-ttu-id="4a533-148">値</span><span class="sxs-lookup"><span data-stu-id="4a533-148">Value</span></span>|  
    |------------|--------------|-----------|  
    |<span data-ttu-id="4a533-149">Form1</span><span class="sxs-lookup"><span data-stu-id="4a533-149">Form1</span></span>|<span data-ttu-id="4a533-150">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="4a533-150">AccessibleDescription</span></span>|<span data-ttu-id="4a533-151">オーダー フォーム</span><span class="sxs-lookup"><span data-stu-id="4a533-151">Order form</span></span>|  
    ||<span data-ttu-id="4a533-152">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="4a533-152">AccessibleName</span></span>|<span data-ttu-id="4a533-153">オーダー フォーム</span><span class="sxs-lookup"><span data-stu-id="4a533-153">Order form</span></span>|  
    ||<span data-ttu-id="4a533-154">フォント サイズ</span><span class="sxs-lookup"><span data-stu-id="4a533-154">Font Size</span></span>|<span data-ttu-id="4a533-155">10</span><span class="sxs-lookup"><span data-stu-id="4a533-155">10</span></span>|  
    ||<span data-ttu-id="4a533-156">テキスト</span><span class="sxs-lookup"><span data-stu-id="4a533-156">Text</span></span>|<span data-ttu-id="4a533-157">ピザ オーダー フォーム</span><span class="sxs-lookup"><span data-stu-id="4a533-157">Pizza Order Form</span></span>|  
    |<span data-ttu-id="4a533-158">PictureBox</span><span class="sxs-lookup"><span data-stu-id="4a533-158">PictureBox</span></span>|<span data-ttu-id="4a533-159">名前</span><span class="sxs-lookup"><span data-stu-id="4a533-159">Name</span></span>|<span data-ttu-id="4a533-160">ロゴ</span><span class="sxs-lookup"><span data-stu-id="4a533-160">logo</span></span>|  
    ||<span data-ttu-id="4a533-161">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="4a533-161">AccessibleDescription</span></span>|<span data-ttu-id="4a533-162">ピザのスライス</span><span class="sxs-lookup"><span data-stu-id="4a533-162">A slice of pizza</span></span>|  
    ||<span data-ttu-id="4a533-163">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="4a533-163">AccessibleName</span></span>|<span data-ttu-id="4a533-164">会社のロゴ</span><span class="sxs-lookup"><span data-stu-id="4a533-164">Company logo</span></span>|  
    ||<span data-ttu-id="4a533-165">イメージ</span><span class="sxs-lookup"><span data-stu-id="4a533-165">Image</span></span>|<span data-ttu-id="4a533-166">任意のアイコンまたはビットマップ</span><span class="sxs-lookup"><span data-stu-id="4a533-166">Any icon or bitmap</span></span>|  
    |<span data-ttu-id="4a533-167">ラベル</span><span class="sxs-lookup"><span data-stu-id="4a533-167">Label</span></span>|<span data-ttu-id="4a533-168">名前</span><span class="sxs-lookup"><span data-stu-id="4a533-168">Name</span></span>|<span data-ttu-id="4a533-169">companyLabel</span><span class="sxs-lookup"><span data-stu-id="4a533-169">companyLabel</span></span>|  
    ||<span data-ttu-id="4a533-170">テキスト</span><span class="sxs-lookup"><span data-stu-id="4a533-170">Text</span></span>|<span data-ttu-id="4a533-171">おいしいピザ</span><span class="sxs-lookup"><span data-stu-id="4a533-171">Good Pizza</span></span>|  
    ||<span data-ttu-id="4a533-172">TabIndex</span><span class="sxs-lookup"><span data-stu-id="4a533-172">TabIndex</span></span>|<span data-ttu-id="4a533-173">1</span><span class="sxs-lookup"><span data-stu-id="4a533-173">1</span></span>|  
    ||<span data-ttu-id="4a533-174">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="4a533-174">AccessibleDescription</span></span>|<span data-ttu-id="4a533-175">会社名</span><span class="sxs-lookup"><span data-stu-id="4a533-175">Company name</span></span>|  
    ||<span data-ttu-id="4a533-176">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="4a533-176">AccessibleName</span></span>|<span data-ttu-id="4a533-177">会社名</span><span class="sxs-lookup"><span data-stu-id="4a533-177">Company name</span></span>|  
    ||<span data-ttu-id="4a533-178">背景色</span><span class="sxs-lookup"><span data-stu-id="4a533-178">Backcolor</span></span>|<span data-ttu-id="4a533-179">青</span><span class="sxs-lookup"><span data-stu-id="4a533-179">Blue</span></span>|  
    ||<span data-ttu-id="4a533-180">前景色</span><span class="sxs-lookup"><span data-stu-id="4a533-180">Forecolor</span></span>|<span data-ttu-id="4a533-181">黄</span><span class="sxs-lookup"><span data-stu-id="4a533-181">Yellow</span></span>|  
    ||<span data-ttu-id="4a533-182">Font Size</span><span class="sxs-lookup"><span data-stu-id="4a533-182">Font size</span></span>|<span data-ttu-id="4a533-183">18</span><span class="sxs-lookup"><span data-stu-id="4a533-183">18</span></span>|  
    |<span data-ttu-id="4a533-184">ラベル</span><span class="sxs-lookup"><span data-stu-id="4a533-184">Label</span></span>|<span data-ttu-id="4a533-185">名前</span><span class="sxs-lookup"><span data-stu-id="4a533-185">Name</span></span>|<span data-ttu-id="4a533-186">customerLabel</span><span class="sxs-lookup"><span data-stu-id="4a533-186">customerLabel</span></span>|  
    ||<span data-ttu-id="4a533-187">テキスト</span><span class="sxs-lookup"><span data-stu-id="4a533-187">Text</span></span>|<span data-ttu-id="4a533-188">名前(&N)</span><span class="sxs-lookup"><span data-stu-id="4a533-188">&Name</span></span>|  
    ||<span data-ttu-id="4a533-189">TabIndex</span><span class="sxs-lookup"><span data-stu-id="4a533-189">TabIndex</span></span>|<span data-ttu-id="4a533-190">2</span><span class="sxs-lookup"><span data-stu-id="4a533-190">2</span></span>|  
    ||<span data-ttu-id="4a533-191">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="4a533-191">AccessibleDescription</span></span>|<span data-ttu-id="4a533-192">顧客名のラベル</span><span class="sxs-lookup"><span data-stu-id="4a533-192">Customer name label</span></span>|  
    ||<span data-ttu-id="4a533-193">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="4a533-193">AccessibleName</span></span>|<span data-ttu-id="4a533-194">顧客名のラベル</span><span class="sxs-lookup"><span data-stu-id="4a533-194">Customer name label</span></span>|  
    ||<span data-ttu-id="4a533-195">UseMnemonic</span><span class="sxs-lookup"><span data-stu-id="4a533-195">UseMnemonic</span></span>|<span data-ttu-id="4a533-196">True</span><span class="sxs-lookup"><span data-stu-id="4a533-196">True</span></span>|  
    |<span data-ttu-id="4a533-197">TextBox</span><span class="sxs-lookup"><span data-stu-id="4a533-197">TextBox</span></span>|<span data-ttu-id="4a533-198">名前</span><span class="sxs-lookup"><span data-stu-id="4a533-198">Name</span></span>|<span data-ttu-id="4a533-199">CustomerName</span><span class="sxs-lookup"><span data-stu-id="4a533-199">customerName</span></span>|  
    ||<span data-ttu-id="4a533-200">テキスト</span><span class="sxs-lookup"><span data-stu-id="4a533-200">Text</span></span>|<span data-ttu-id="4a533-201">(なし)</span><span class="sxs-lookup"><span data-stu-id="4a533-201">(none)</span></span>|  
    ||<span data-ttu-id="4a533-202">TabIndex</span><span class="sxs-lookup"><span data-stu-id="4a533-202">TabIndex</span></span>|<span data-ttu-id="4a533-203">3</span><span class="sxs-lookup"><span data-stu-id="4a533-203">3</span></span>|  
    ||<span data-ttu-id="4a533-204">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="4a533-204">AccessibleDescription</span></span>|<span data-ttu-id="4a533-205">顧客名</span><span class="sxs-lookup"><span data-stu-id="4a533-205">Customer name</span></span>|  
    ||<span data-ttu-id="4a533-206">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="4a533-206">AccessibleName</span></span>|<span data-ttu-id="4a533-207">顧客名</span><span class="sxs-lookup"><span data-stu-id="4a533-207">Customer name</span></span>|  
    |<span data-ttu-id="4a533-208">GroupBox</span><span class="sxs-lookup"><span data-stu-id="4a533-208">GroupBox</span></span>|<span data-ttu-id="4a533-209">名前</span><span class="sxs-lookup"><span data-stu-id="4a533-209">Name</span></span>|<span data-ttu-id="4a533-210">sizeOptions</span><span class="sxs-lookup"><span data-stu-id="4a533-210">sizeOptions</span></span>|  
    ||<span data-ttu-id="4a533-211">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="4a533-211">AccessibleDescription</span></span>|<span data-ttu-id="4a533-212">ピザのサイズ オプション</span><span class="sxs-lookup"><span data-stu-id="4a533-212">Pizza size options</span></span>|  
    ||<span data-ttu-id="4a533-213">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="4a533-213">AccessibleName</span></span>|<span data-ttu-id="4a533-214">ピザのサイズ オプション</span><span class="sxs-lookup"><span data-stu-id="4a533-214">Pizza size options</span></span>|  
    ||<span data-ttu-id="4a533-215">テキスト</span><span class="sxs-lookup"><span data-stu-id="4a533-215">Text</span></span>|<span data-ttu-id="4a533-216">ピザのサイズ</span><span class="sxs-lookup"><span data-stu-id="4a533-216">Pizza size</span></span>|  
    ||<span data-ttu-id="4a533-217">TabIndex</span><span class="sxs-lookup"><span data-stu-id="4a533-217">TabIndex</span></span>|<span data-ttu-id="4a533-218">4</span><span class="sxs-lookup"><span data-stu-id="4a533-218">4</span></span>|  
    |<span data-ttu-id="4a533-219">RadioButton</span><span class="sxs-lookup"><span data-stu-id="4a533-219">RadioButton</span></span>|<span data-ttu-id="4a533-220">名前</span><span class="sxs-lookup"><span data-stu-id="4a533-220">Name</span></span>|<span data-ttu-id="4a533-221">smallPizza</span><span class="sxs-lookup"><span data-stu-id="4a533-221">smallPizza</span></span>|  
    ||<span data-ttu-id="4a533-222">テキスト</span><span class="sxs-lookup"><span data-stu-id="4a533-222">Text</span></span>|<span data-ttu-id="4a533-223">スモール(&S) $6.00</span><span class="sxs-lookup"><span data-stu-id="4a533-223">&Small $6.00</span></span>|  
    ||<span data-ttu-id="4a533-224">チェック済み</span><span class="sxs-lookup"><span data-stu-id="4a533-224">Checked</span></span>|<span data-ttu-id="4a533-225">True</span><span class="sxs-lookup"><span data-stu-id="4a533-225">True</span></span>|  
    ||<span data-ttu-id="4a533-226">TabIndex</span><span class="sxs-lookup"><span data-stu-id="4a533-226">TabIndex</span></span>|<span data-ttu-id="4a533-227">0</span><span class="sxs-lookup"><span data-stu-id="4a533-227">0</span></span>|  
    ||<span data-ttu-id="4a533-228">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="4a533-228">AccessibleDescription</span></span>|<span data-ttu-id="4a533-229">Small pizza</span><span class="sxs-lookup"><span data-stu-id="4a533-229">Small pizza</span></span>|  
    ||<span data-ttu-id="4a533-230">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="4a533-230">AccessibleName</span></span>|<span data-ttu-id="4a533-231">Small pizza</span><span class="sxs-lookup"><span data-stu-id="4a533-231">Small pizza</span></span>|  
    |<span data-ttu-id="4a533-232">RadioButton</span><span class="sxs-lookup"><span data-stu-id="4a533-232">RadioButton</span></span>|<span data-ttu-id="4a533-233">名前</span><span class="sxs-lookup"><span data-stu-id="4a533-233">Name</span></span>|<span data-ttu-id="4a533-234">largePizza</span><span class="sxs-lookup"><span data-stu-id="4a533-234">largePizza</span></span>|  
    ||<span data-ttu-id="4a533-235">テキスト</span><span class="sxs-lookup"><span data-stu-id="4a533-235">Text</span></span>|<span data-ttu-id="4a533-236">ラージ(&L) $10.00</span><span class="sxs-lookup"><span data-stu-id="4a533-236">&Large $10.00</span></span>|  
    ||<span data-ttu-id="4a533-237">TabIndex</span><span class="sxs-lookup"><span data-stu-id="4a533-237">TabIndex</span></span>|<span data-ttu-id="4a533-238">1</span><span class="sxs-lookup"><span data-stu-id="4a533-238">1</span></span>|  
    ||<span data-ttu-id="4a533-239">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="4a533-239">AccessibleDescription</span></span>|<span data-ttu-id="4a533-240">ラージ サイズのピザ</span><span class="sxs-lookup"><span data-stu-id="4a533-240">Large pizza</span></span>|  
    ||<span data-ttu-id="4a533-241">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="4a533-241">AccessibleName</span></span>|<span data-ttu-id="4a533-242">ラージ サイズのピザ</span><span class="sxs-lookup"><span data-stu-id="4a533-242">Large pizza</span></span>|  
    |<span data-ttu-id="4a533-243">ラベル</span><span class="sxs-lookup"><span data-stu-id="4a533-243">Label</span></span>|<span data-ttu-id="4a533-244">名前</span><span class="sxs-lookup"><span data-stu-id="4a533-244">Name</span></span>|<span data-ttu-id="4a533-245">toppingsLabel</span><span class="sxs-lookup"><span data-stu-id="4a533-245">toppingsLabel</span></span>|  
    ||<span data-ttu-id="4a533-246">テキスト</span><span class="sxs-lookup"><span data-stu-id="4a533-246">Text</span></span>|<span data-ttu-id="4a533-247">トッピング(&T) (1 つ $0.75)</span><span class="sxs-lookup"><span data-stu-id="4a533-247">&Toppings ($0.75 each)</span></span>|  
    ||<span data-ttu-id="4a533-248">TabIndex</span><span class="sxs-lookup"><span data-stu-id="4a533-248">TabIndex</span></span>|<span data-ttu-id="4a533-249">5</span><span class="sxs-lookup"><span data-stu-id="4a533-249">5</span></span>|  
    ||<span data-ttu-id="4a533-250">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="4a533-250">AccessibleDescription</span></span>|<span data-ttu-id="4a533-251">トッピング ラベル</span><span class="sxs-lookup"><span data-stu-id="4a533-251">Toppings label</span></span>|  
    ||<span data-ttu-id="4a533-252">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="4a533-252">AccessibleName</span></span>|<span data-ttu-id="4a533-253">トッピング ラベル</span><span class="sxs-lookup"><span data-stu-id="4a533-253">Toppings label</span></span>|  
    ||<span data-ttu-id="4a533-254">UseMnemonic</span><span class="sxs-lookup"><span data-stu-id="4a533-254">UseMnemonic</span></span>|<span data-ttu-id="4a533-255">True</span><span class="sxs-lookup"><span data-stu-id="4a533-255">True</span></span>|  
    |<span data-ttu-id="4a533-256">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="4a533-256">CheckedListBox</span></span>|<span data-ttu-id="4a533-257">名前</span><span class="sxs-lookup"><span data-stu-id="4a533-257">Name</span></span>|<span data-ttu-id="4a533-258">トッピング</span><span class="sxs-lookup"><span data-stu-id="4a533-258">toppings</span></span>|  
    ||<span data-ttu-id="4a533-259">TabIndex</span><span class="sxs-lookup"><span data-stu-id="4a533-259">TabIndex</span></span>|<span data-ttu-id="4a533-260">6</span><span class="sxs-lookup"><span data-stu-id="4a533-260">6</span></span>|  
    ||<span data-ttu-id="4a533-261">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="4a533-261">AccessibleDescription</span></span>|<span data-ttu-id="4a533-262">選択可能なトッピング</span><span class="sxs-lookup"><span data-stu-id="4a533-262">Available toppings</span></span>|  
    ||<span data-ttu-id="4a533-263">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="4a533-263">AccessibleName</span></span>|<span data-ttu-id="4a533-264">選択可能なトッピング</span><span class="sxs-lookup"><span data-stu-id="4a533-264">Available toppings</span></span>|  
    ||<span data-ttu-id="4a533-265">項目</span><span class="sxs-lookup"><span data-stu-id="4a533-265">Items</span></span>|<span data-ttu-id="4a533-266">ペペロニ、ソーセージ、マッシュルーム</span><span class="sxs-lookup"><span data-stu-id="4a533-266">Pepperoni, Sausage, Mushrooms</span></span>|  
    |<span data-ttu-id="4a533-267">ボタン</span><span class="sxs-lookup"><span data-stu-id="4a533-267">Button</span></span>|<span data-ttu-id="4a533-268">名前</span><span class="sxs-lookup"><span data-stu-id="4a533-268">Name</span></span>|<span data-ttu-id="4a533-269">順序</span><span class="sxs-lookup"><span data-stu-id="4a533-269">order</span></span>|  
    ||<span data-ttu-id="4a533-270">テキスト</span><span class="sxs-lookup"><span data-stu-id="4a533-270">Text</span></span>|<span data-ttu-id="4a533-271">順序(&O)</span><span class="sxs-lookup"><span data-stu-id="4a533-271">&Order</span></span>|  
    ||<span data-ttu-id="4a533-272">TabIndex</span><span class="sxs-lookup"><span data-stu-id="4a533-272">TabIndex</span></span>|<span data-ttu-id="4a533-273">7</span><span class="sxs-lookup"><span data-stu-id="4a533-273">7</span></span>|  
    ||<span data-ttu-id="4a533-274">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="4a533-274">AccessibleDescription</span></span>|<span data-ttu-id="4a533-275">注文の合計</span><span class="sxs-lookup"><span data-stu-id="4a533-275">Total the order</span></span>|  
    ||<span data-ttu-id="4a533-276">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="4a533-276">AccessibleName</span></span>|<span data-ttu-id="4a533-277">注文の合計</span><span class="sxs-lookup"><span data-stu-id="4a533-277">Total order</span></span>|  
    |<span data-ttu-id="4a533-278">ボタン</span><span class="sxs-lookup"><span data-stu-id="4a533-278">Button</span></span>|<span data-ttu-id="4a533-279">名前</span><span class="sxs-lookup"><span data-stu-id="4a533-279">Name</span></span>|<span data-ttu-id="4a533-280">cancel</span><span class="sxs-lookup"><span data-stu-id="4a533-280">cancel</span></span>|  
    ||<span data-ttu-id="4a533-281">テキスト</span><span class="sxs-lookup"><span data-stu-id="4a533-281">Text</span></span>|<span data-ttu-id="4a533-282">キャンセル(&C)</span><span class="sxs-lookup"><span data-stu-id="4a533-282">&Cancel</span></span>|  
    ||<span data-ttu-id="4a533-283">TabIndex</span><span class="sxs-lookup"><span data-stu-id="4a533-283">TabIndex</span></span>|<span data-ttu-id="4a533-284">9</span><span class="sxs-lookup"><span data-stu-id="4a533-284">8</span></span>|  
    ||<span data-ttu-id="4a533-285">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="4a533-285">AccessibleDescription</span></span>|<span data-ttu-id="4a533-286">注文のキャンセル</span><span class="sxs-lookup"><span data-stu-id="4a533-286">Cancel the order</span></span>|  
    ||<span data-ttu-id="4a533-287">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="4a533-287">AccessibleName</span></span>|<span data-ttu-id="4a533-288">注文のキャンセル</span><span class="sxs-lookup"><span data-stu-id="4a533-288">Cancel order</span></span>|  
    |<span data-ttu-id="4a533-289">MainMenu</span><span class="sxs-lookup"><span data-stu-id="4a533-289">MainMenu</span></span>|<span data-ttu-id="4a533-290">名前</span><span class="sxs-lookup"><span data-stu-id="4a533-290">Name</span></span>|<span data-ttu-id="4a533-291">theMainMenu</span><span class="sxs-lookup"><span data-stu-id="4a533-291">theMainMenu</span></span>|  
    |<span data-ttu-id="4a533-292">MenuItem</span><span class="sxs-lookup"><span data-stu-id="4a533-292">MenuItem</span></span>|<span data-ttu-id="4a533-293">名前</span><span class="sxs-lookup"><span data-stu-id="4a533-293">Name</span></span>|<span data-ttu-id="4a533-294">fileCommands</span><span class="sxs-lookup"><span data-stu-id="4a533-294">fileCommands</span></span>|  
    ||<span data-ttu-id="4a533-295">テキスト</span><span class="sxs-lookup"><span data-stu-id="4a533-295">Text</span></span>|<span data-ttu-id="4a533-296">ファイル(&F)</span><span class="sxs-lookup"><span data-stu-id="4a533-296">&File</span></span>|  
    |<span data-ttu-id="4a533-297">MenuItem</span><span class="sxs-lookup"><span data-stu-id="4a533-297">MenuItem</span></span>|<span data-ttu-id="4a533-298">名前</span><span class="sxs-lookup"><span data-stu-id="4a533-298">Name</span></span>|<span data-ttu-id="4a533-299">exitApp</span><span class="sxs-lookup"><span data-stu-id="4a533-299">exitApp</span></span>|  
    ||<span data-ttu-id="4a533-300">テキスト</span><span class="sxs-lookup"><span data-stu-id="4a533-300">Text</span></span>|<span data-ttu-id="4a533-301">終了(&X)</span><span class="sxs-lookup"><span data-stu-id="4a533-301">E&xit</span></span>|  
  
     <span data-ttu-id="4a533-302">![ピザ オーダー フォーム](../../../../docs/framework/winforms/advanced/media/vbpizzaorderform.gif "vbPizzaOrderForm")</span><span class="sxs-lookup"><span data-stu-id="4a533-302">![Pizza Order Form](../../../../docs/framework/winforms/advanced/media/vbpizzaorderform.gif "vbPizzaOrderForm")</span></span>  
<span data-ttu-id="4a533-303">フォームは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="4a533-303">Your form will look something like the following:</span></span>  
  
## <a name="supporting-high-contrast-mode"></a><span data-ttu-id="4a533-304">ハイ コントラスト モードのサポート</span><span class="sxs-lookup"><span data-stu-id="4a533-304">Supporting High Contrast Mode</span></span>  
 <span data-ttu-id="4a533-305">ハイコントラスト モードとは、視覚的に障碍のあるユーザーの役に立つ対照的な色とフォント サイズを使用して、読みやすさを向上する Windows のシステム設定です。</span><span class="sxs-lookup"><span data-stu-id="4a533-305">High Contrast mode is a Windows system setting that improves readability by using contrasting colors and font sizes that are beneficial for visually impaired users.</span></span> <span data-ttu-id="4a533-306"><xref:System.Windows.Forms.SystemInformation.HighContrast%2A>ハイ コントラスト モードが設定されているかどうかを決定するプロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="4a533-306">The <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> property is provided to determine whether the High Contrast mode is set.</span></span>  
  
 <span data-ttu-id="4a533-307">SystemInformation.HighContrast が `true` の場合、アプリケーションは次のようになります</span><span class="sxs-lookup"><span data-stu-id="4a533-307">If SystemInformation.HighContrast is `true`, the application should:</span></span>  
  
-   <span data-ttu-id="4a533-308">システムの配色を使用して、すべてのユーザー インターフェイス要素を表示します。</span><span class="sxs-lookup"><span data-stu-id="4a533-308">Display all user interface elements using the system color scheme</span></span>  
  
-   <span data-ttu-id="4a533-309">色で伝達される情報を、視覚的手掛かりまたはサウンドで伝達します。</span><span class="sxs-lookup"><span data-stu-id="4a533-309">Convey by visual cues or sound any information that is conveyed through color.</span></span> <span data-ttu-id="4a533-310">たとえば、特定のリスト項目が赤いフォントを使用して強調表示されている場合に、フォントに太字を追加することで、項目が強調されていることをユーザーが色以外の手掛かりで確認できます。</span><span class="sxs-lookup"><span data-stu-id="4a533-310">For example, if particular list items are highlighted by using a red font, you could also add bold to the font, so that the user has a non-color cue that the items are highlighted.</span></span>  
  
-   <span data-ttu-id="4a533-311">テキストの背後にあるイメージやパターンを省略します。</span><span class="sxs-lookup"><span data-stu-id="4a533-311">Omit any images or patterns behind text</span></span>  
  
 <span data-ttu-id="4a533-312">アプリケーションが開始し、システム イベント <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> に応答する際、アプリケーションで <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> の設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a533-312">The application should check the setting of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> when the application starts and respond to the system event <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span></span> <span data-ttu-id="4a533-313"><xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> イベントは、<xref:System.Windows.Forms.SystemInformation.HighContrast%2A> の値が変更されるたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="4a533-313">The <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event is raised whenever the value of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> changes.</span></span>  
  
 <span data-ttu-id="4a533-314">この例のアプリケーションでは、色のシステム設定を使用していない唯一の要素は `lblCompanyName` です。</span><span class="sxs-lookup"><span data-stu-id="4a533-314">In our application, the only element that is not using the system settings for color is `lblCompanyName`.</span></span> <span data-ttu-id="4a533-315"><xref:System.Drawing.SystemColors>クラスを使用してラベルの色の設定をユーザーが選択したシステム カラーに変更します。</span><span class="sxs-lookup"><span data-stu-id="4a533-315">The <xref:System.Drawing.SystemColors> class is used to change the color settings of the label to the user-selected system colors.</span></span>  
  
#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a><span data-ttu-id="4a533-316">効果的な方法でハイ コントラスト モードを有効にするには</span><span class="sxs-lookup"><span data-stu-id="4a533-316">To enable High Contrast mode in an effective way</span></span>  
  
1.  <span data-ttu-id="4a533-317">ラベルの色をシステム カラーを設定するメソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="4a533-317">Create a method to set the colors of the label to the system colors.</span></span>  
  
    ```  
    ' Visual Basic  
    Private Sub SetColorScheme()  
       If SystemInformation.HighContrast Then  
          companyLabel.BackColor = SystemColors.Window  
          companyLabel.ForeColor = SystemColors.WindowText  
       Else  
          companyLabel.BackColor = Color.Blue  
          companyLabel.ForeColor = Color.Yellow  
       End If  
    End Sub  
  
    // C#  
    private void SetColorScheme()  
    {  
       if (SystemInformation.HighContrast)  
       {  
          companyLabel.BackColor = SystemColors.Window;  
          companyLabel.ForeColor = SystemColors.WindowText;  
       }  
       else  
       {  
          companyLabel.BackColor = Color.Blue;  
          companyLabel.ForeColor = Color.Yellow;  
       }  
    }  
    ```  
  
2.  <span data-ttu-id="4a533-318">フォームのコンストラクターで `SetColorScheme` プロシージャを呼び出します (Visual Basic では `Public Sub New()`、Visual C# では `public class Form1`)。</span><span class="sxs-lookup"><span data-stu-id="4a533-318">Call the `SetColorScheme` procedure in the form constructor (`Public Sub New()` in Visual Basic and `public class Form1` in Visual C#).</span></span> <span data-ttu-id="4a533-319">Visual Basic でコンストラクターにアクセスするには、**Windows フォーム デザイナーで生成されたコード**というラベルが付いた領域を展開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a533-319">To access the constructor in Visual Basic, you will need to expand the region labeled **Windows Form Designer generated code**.</span></span>  
  
    ```  
    ' Visual Basic   
    Public Sub New()  
       MyBase.New()  
       InitializeComponent()  
       SetColorScheme()  
    End Sub  
  
    // C#  
    public Form1()  
    {  
       InitializeComponent();  
       SetColorScheme();  
    }  
    ```  
  
3.  <span data-ttu-id="4a533-320">適切なシグネチャを持つイベント プロシージャを作成して、<xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> イベントに対応します。</span><span class="sxs-lookup"><span data-stu-id="4a533-320">Create an event procedure, with the appropriate signature, to respond to the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event.</span></span>  
  
    ```  
    ' Visual Basic  
    Protected Sub UserPreferenceChanged(ByVal sender As Object, _  
    ByVal e As Microsoft.Win32.UserPreferenceChangedEventArgs)  
       SetColorScheme()  
    End Sub  
  
    // C#  
    public void UserPreferenceChanged(object sender,   
    Microsoft.Win32.UserPreferenceChangedEventArgs e)  
    {  
       SetColorScheme();  
    }  
    ```  
  
4.  <span data-ttu-id="4a533-321">`InitializeComponents` への呼び出しの後でコードをフォームのコンストラクターに追加して、イベント プロシージャをシステム イベントにフックします。</span><span class="sxs-lookup"><span data-stu-id="4a533-321">Add code to the form constructor, after the call to `InitializeComponents`, to hook up the event procedure to the system event.</span></span> <span data-ttu-id="4a533-322">このメソッドは `SetColorScheme` プロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4a533-322">This method calls the `SetColorScheme` procedure.</span></span>  
  
    ```  
    ' Visual Basic  
    Public Sub New()  
       MyBase.New()  
       InitializeComponent()  
       SetColorScheme()  
       AddHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _  
          AddressOf Me.UserPreferenceChanged  
    End Sub  
  
    // C#  
    public Form1()  
    {  
       InitializeComponent();  
       SetColorScheme();  
       Microsoft.Win32.SystemEvents.UserPreferenceChanged   
          += new Microsoft.Win32.UserPreferenceChangedEventHandler(  
          this.UserPreferenceChanged);  
    }  
    ```  
  
5.  <span data-ttu-id="4a533-323">基本クラスの <xref:System.Windows.Forms.Control.Dispose%2A> メソッドへの呼び出しの前に、フォームの <xref:System.Windows.Forms.Control.Dispose%2A> メソッドにコードを追加して、アプリケーションの終了時にイベントを解放します。</span><span class="sxs-lookup"><span data-stu-id="4a533-323">Add code to the form <xref:System.Windows.Forms.Control.Dispose%2A> method, before the call to the <xref:System.Windows.Forms.Control.Dispose%2A> method of the base class, to release the event when the application closes.</span></span> <span data-ttu-id="4a533-324">Visual Basic で <xref:System.Windows.Forms.Control.Dispose%2A> メソッドにアクセスするには、「Windows フォーム デザイナーで生成されたコード」というラベルが付いた領域を展開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a533-324">To access the <xref:System.Windows.Forms.Control.Dispose%2A> method in Visual Basic, you will need to expand the region labeled Windows Form Designer generated code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4a533-325">システム イベントのコードが、メイン アプリケーションとは別のスレッドを実行します。</span><span class="sxs-lookup"><span data-stu-id="4a533-325">The system event code runs a thread separate from the main application.</span></span> <span data-ttu-id="4a533-326">イベントを解放しないと、プログラムが終了した後でも、イベントにフックするコードが実行されます。</span><span class="sxs-lookup"><span data-stu-id="4a533-326">If you do not release the event, the code that you hook up to the event will run even after the program is closed.</span></span>  
  
    ```  
    ' Visual Basic  
    Protected Overloads Overrides Sub Dispose(ByVal disposing As Boolean)  
       If disposing Then  
          If Not (components Is Nothing) Then  
             components.Dispose()  
          End If  
       End If  
       RemoveHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _  
          AddressOf Me.UserPreferenceChanged  
       MyBase.Dispose(disposing)  
    End Sub  
  
    // C#  
    protected override void Dispose( bool disposing )  
    {  
       if( disposing )  
       {  
          if (components != null)   
          {  
             components.Dispose();  
          }  
       }  
       Microsoft.Win32.SystemEvents.UserPreferenceChanged   
          -= new Microsoft.Win32.UserPreferenceChangedEventHandler(  
          this.UserPreferenceChanged);  
       base.Dispose( disposing );  
    }  
    ```  
  
6.  <span data-ttu-id="4a533-327">F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="4a533-327">Press F5 to run the application.</span></span>  
  
## <a name="conveying-important-information-by-means-other-than-sound"></a><span data-ttu-id="4a533-328">サウンド以外の方法で重要な情報を伝達する</span><span class="sxs-lookup"><span data-stu-id="4a533-328">Conveying Important Information by Means Other Than Sound</span></span>  
 <span data-ttu-id="4a533-329">このアプリケーションでは、サウンドだけで伝達される情報はありません。</span><span class="sxs-lookup"><span data-stu-id="4a533-329">In this application, no information is conveyed by sound alone.</span></span> <span data-ttu-id="4a533-330">アプリケーションでサウンドを使用する場合は、別の方法もで情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a533-330">If you use sound in your application, then you should supply the information by some other means as well.</span></span>  
  
#### <a name="to-supply-information-by-some-other-means-than-sound"></a><span data-ttu-id="4a533-331">サウンド以外の方法で情報を提供するには</span><span class="sxs-lookup"><span data-stu-id="4a533-331">To supply information by some other means than sound</span></span>  
  
1.  <span data-ttu-id="4a533-332">Windows API 関数 FlashWindow を使用して、タイトル バーをフラッシュさせます。</span><span class="sxs-lookup"><span data-stu-id="4a533-332">Make the title bar flash by using the Windows API function FlashWindow.</span></span> <span data-ttu-id="4a533-333">Windows API 関数を呼び出す方法の例は、「[チュートリアル: Windows API の呼び出し](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a533-333">For an example of how to call Windows API functions, see [Walkthrough: Calling Windows APIs](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4a533-334">ユーザーが Windows SoundSentry サービスを有効にして、コンピューターの内蔵スピーカーを通じてシステム サウンドが再生されるときにウィンドウをフラッシュさせていることがあります。</span><span class="sxs-lookup"><span data-stu-id="4a533-334">The user may have the Windows SoundSentry service enabled, which will also cause the window to flash when the system sounds are played through the computer's built-in speaker.</span></span>  
  
2.  <span data-ttu-id="4a533-335">ユーザーがそれに応答できるように、非モーダル ウィンドウで重要な情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="4a533-335">Display the important information in a non-modal window so that the user may respond to it.</span></span>  
  
3.  <span data-ttu-id="4a533-336">キーボード フォーカスを取得するメッセージ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="4a533-336">Display a message box that acquires the keyboard focus.</span></span> <span data-ttu-id="4a533-337">ユーザーが入力しているときは、このメソッドは回避します。</span><span class="sxs-lookup"><span data-stu-id="4a533-337">Avoid this method when the user may be typing.</span></span>  
  
4.  <span data-ttu-id="4a533-338">タスクバーの状態通知領域に状態インジケーターを表示します。</span><span class="sxs-lookup"><span data-stu-id="4a533-338">Display a status indicator in the status notification area of the taskbar.</span></span> <span data-ttu-id="4a533-339">詳細については、「[Windows フォームの NotifyIcon コンポーネントによるタスクバーへのアプリケーション アイコンの追加](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a533-339">For details, see [Adding Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
## <a name="testing-the-application"></a><span data-ttu-id="4a533-340">アプリケーションのテスト</span><span class="sxs-lookup"><span data-stu-id="4a533-340">Testing the Application</span></span>  
 <span data-ttu-id="4a533-341">アプリケーションを配置する前に、実装したユーザー補助機能をテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a533-341">Before deploying the application, you should test the accessibility features that you have implemented.</span></span>  
  
#### <a name="to-test-accessibility-features"></a><span data-ttu-id="4a533-342">ユーザー補助機能をテストするには</span><span class="sxs-lookup"><span data-stu-id="4a533-342">To test accessibility features</span></span>  
  
1.  <span data-ttu-id="4a533-343">キーボード アクセスをテストするには、マウスを外し、キーボードのみを使用して各機能のユーザー インターフェイスを移動します。</span><span class="sxs-lookup"><span data-stu-id="4a533-343">To test keyboard access, unplug the mouse and navigate the user interface for each feature using only the keyboard.</span></span> <span data-ttu-id="4a533-344">キーボードのみを使用してすべてのタスクが実行できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4a533-344">Ensure that all tasks may be performed using the keyboard only.</span></span>  
  
2.  <span data-ttu-id="4a533-345">ハイ コントラストのサポートをテストするには、コントロール パネルの [ユーザー補助のオプション] アイコンを選択します。</span><span class="sxs-lookup"><span data-stu-id="4a533-345">To test support of High Contrast, choose the Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="4a533-346">[表示] タブをクリックし、[ハイ コントラストを使用する] チェック ボックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="4a533-346">Click the Display tab and select the Use High Contrast check box.</span></span> <span data-ttu-id="4a533-347">色とフォントの変更が反映されることを確認するために、すべてのユーザー インターフェイス要素を移動します。</span><span class="sxs-lookup"><span data-stu-id="4a533-347">Navigate through all user interface elements to ensure that the color and font changes are reflected.</span></span> <span data-ttu-id="4a533-348">また、テキストの背景に描画されるイメージやパターンが省略されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4a533-348">Also, ensure that images or patterns drawn behind text are omitted.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4a533-349">Windows NT 4 では、コントロール パネルにユーザー補助機能オプション アイコンがありません。</span><span class="sxs-lookup"><span data-stu-id="4a533-349">Windows NT 4 does not have an Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="4a533-350">したがって、SystemInformation.HighContrast の設定変更のこの手順は、Windows NT 4 では機能しません。</span><span class="sxs-lookup"><span data-stu-id="4a533-350">Thus, this procedure for changing the SystemInformation.HighContrast setting does not work in Windows NT 4.</span></span>  
  
3.  <span data-ttu-id="4a533-351">その他のツールは、アプリケーションのユーザー補助機能をテストするためにすぐに使用できます。</span><span class="sxs-lookup"><span data-stu-id="4a533-351">Other tools are readily available for testing the accessibility of an application.</span></span>  
  
4.  <span data-ttu-id="4a533-352">キーボード フォーカスを公開することをテストするには、拡大鏡を実行します。</span><span class="sxs-lookup"><span data-stu-id="4a533-352">To test exposing the keyboard focus, run Magnifier.</span></span> <span data-ttu-id="4a533-353">(拡大鏡を開くには、**[スタート]** メニューをクリックし、**[すべてのプログラム]**、**[アクセサリ]**、**[アクセシビリティ]** の順でポイントして、**[拡大鏡]** をクリックします)。</span><span class="sxs-lookup"><span data-stu-id="4a533-353">(To open it, click the **Start** menu, point to **Programs**, point to **Accessories**, point to **Accessibility**, and then click **Magnifier**).</span></span> <span data-ttu-id="4a533-354">キーボードの [Tab] キーとマウスの両方を使用して、ユーザー インターフェイスを移動します。</span><span class="sxs-lookup"><span data-stu-id="4a533-354">Navigate the user interface using both keyboard tabbing and the mouse.</span></span> <span data-ttu-id="4a533-355">すべての操作が**拡大鏡**で正常に追跡されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4a533-355">Ensure that all navigation is tracked properly in **Magnifier**.</span></span>  
  
5.  <span data-ttu-id="4a533-356">画面要素の公開をテストするには、検査を実行し、マウスと TAB キーの両方を使用して、各要素に到達します。</span><span class="sxs-lookup"><span data-stu-id="4a533-356">To test exposing screen elements, run Inspect, and use both the mouse and the TAB key to reach each element.</span></span> <span data-ttu-id="4a533-357">[検査] ウィンドウの名前、状態、ロール、場所、および値のフィールドに表示される情報が UI 内の各オブジェクトについて、ユーザーにとって意味があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4a533-357">Ensure that the information presented in the Name, State, Role, Location, and Value fields of the Inspect window is meaningful to the user for each object in the UI.</span></span>
