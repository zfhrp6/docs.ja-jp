---
title: "方法: カスタム アクティビティ テンプレートを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 772ad2a7ea56001bf3ecba089e62d6bc0f59e5ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-activity-template"></a><span data-ttu-id="bb00e-102">方法: カスタム アクティビティ テンプレートを作成する</span><span class="sxs-lookup"><span data-stu-id="bb00e-102">How to: Create a Custom Activity Template</span></span>
<span data-ttu-id="bb00e-103">カスタム複合アクティビティなどのアクティビティの構成のカスタマイズには、カスタム アクティビティ テンプレートが使用されるため、手動で各アクティビティを個別に作成し、そのプロパティおよびその他の設定を構成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="bb00e-103">Custom activity templates are used to customize the configuration of activities, including custom composite activities, so that users do not have to create each activity individually and configure their properties and other settings manually.</span></span> <span data-ttu-id="bb00e-104">これらのカスタム テンプレートで使用できる、**ツールボックス**上、[!INCLUDE[wfd1](../../../includes/wfd1-md.md)]または再ホストされたデザイナーでは、元のユーザーに画面にドラッグできる、構成済みのデザインからです。</span><span class="sxs-lookup"><span data-stu-id="bb00e-104">These custom templates can be made available in the **Toolbox** on the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] or from a rehosted designer, from which users can drag them onto the preconfigured design surface.</span></span> [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]<span data-ttu-id="bb00e-105">このようなテンプレートの良い例が付属しています。 [SendAndReceiveReply テンプレート デザイナー](/visualstudio/workflow-designer/sendandreceivereply-template-designer)と[ReceiveAndSendReply テンプレート デザイナー](/visualstudio/workflow-designer/receiveandsendreply-template-designer)で、[メッセージング アクティビティ デザイナー](/visualstudio/workflow-designer/messaging-activity-designers)カテゴリ。</span><span class="sxs-lookup"><span data-stu-id="bb00e-105"> ships with good examples of such templates: the [SendAndReceiveReply Template Designer](/visualstudio/workflow-designer/sendandreceivereply-template-designer) and the [ReceiveAndSendReply Template Designer](/visualstudio/workflow-designer/receiveandsendreply-template-designer) in the [Messaging Activity Designers](/visualstudio/workflow-designer/messaging-activity-designers) category.</span></span>  
  
 <span data-ttu-id="bb00e-106">このトピックの最初の手順は、カスタム アクティビティ テンプレートを作成する方法を説明、**遅延**アクティビティと 2 番目の手順について簡単にする方法について説明で使用できるように、[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]カスタム テンプレートが機能することを確認します。</span><span class="sxs-lookup"><span data-stu-id="bb00e-106">The first procedure in this topic describes how to create a custom activity template for a **Delay** activity and the second procedure describes briefly how to make it available in a [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] to verify that the custom template works.</span></span>  
  
 <span data-ttu-id="bb00e-107">カスタム アクティビティ テンプレートに <xref:System.Activities.Presentation.IActivityTemplateFactory> を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb00e-107">Custom activity templates must implement the <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span></span> <span data-ttu-id="bb00e-108">このインターフェイスには単一の <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> メソッドがあり、このメソッドを使用して、テンプレートで使用されるアクティビティ インスタンスを作成および構成できます。</span><span class="sxs-lookup"><span data-stu-id="bb00e-108">The interface has a single <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> method with which you can create and configure the activity instances used in the template.</span></span>  
  
### <a name="to-create-a-template-for-the-delay-activity"></a><span data-ttu-id="bb00e-109">Delay アクティビティのテンプレートを作成するには</span><span class="sxs-lookup"><span data-stu-id="bb00e-109">To create a template for the Delay activity</span></span>  
  
1.  <span data-ttu-id="bb00e-110">[!INCLUDE[vs2010](../../../includes/vs2010-md.md)] を起動します。</span><span class="sxs-lookup"><span data-stu-id="bb00e-110">Start [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="bb00e-111">**ファイル**] メニューのをポイント**新規**、し、[**プロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="bb00e-111">On the **File** menu, point to **New**, and then select **Project**.</span></span>  
  
     <span data-ttu-id="bb00e-112">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb00e-112">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="bb00e-113">**プロジェクトの種類**ペインで、**ワークフロー**いずれかから、 **Visual c#**プロジェクトまたは**Visual Basic**に応じてグループ化、言語の優先順位。</span><span class="sxs-lookup"><span data-stu-id="bb00e-113">In the **Project Types** pane, select **Workflow** from either the **Visual C#** projects or **Visual Basic** groupings depending on your language preference.</span></span>  
  
4.  <span data-ttu-id="bb00e-114">**テンプレート**ペインで、**アクティビティ ライブラリ**です。</span><span class="sxs-lookup"><span data-stu-id="bb00e-114">In the **Templates** pane, select **Activity Library**.</span></span>  
  
5.  <span data-ttu-id="bb00e-115">**名前**ボックスに、入力`DelayActivityTemplate`です。</span><span class="sxs-lookup"><span data-stu-id="bb00e-115">In the **Name** box, enter `DelayActivityTemplate`.</span></span>  
  
6.  <span data-ttu-id="bb00e-116">既定値を受け入れます、**場所**と**ソリューション名**テキスト ボックス、およびクリック**[ok]**です。</span><span class="sxs-lookup"><span data-stu-id="bb00e-116">Accept the defaults in the **Location** and **Solution name** text boxes, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="bb00e-117">DelayActivityTemplate プロジェクトの 参照設定 ディレクトリを右クリックして**ソリューション エクスプ ローラー**選択**参照の追加**を開くには、**参照の追加** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="bb00e-117">Right-click the References directory of the DelayActivityTemplate project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>  
  
8.  <span data-ttu-id="bb00e-118">移動、 **.NET**タブおよび選択**PresentationFramework**から、**コンポーネント名**クリックして左列**OK**参照を追加するにはPresentationFramework.dll ファイル。</span><span class="sxs-lookup"><span data-stu-id="bb00e-118">Go to the **.NET** tab and select **PresentationFramework** from the **Component Name** column on the left and click **OK** to add a reference to the PresentationFramework.dll file.</span></span>  
  
9. <span data-ttu-id="bb00e-119">この手順を繰り返して、System.Activities.Presentation.dll ファイルと WindowsBase.dll ファイルへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="bb00e-119">Repeat this procedure to add references to the System.Activities.Presentation.dll and the WindowsBase.dll files.</span></span>  
  
10. <span data-ttu-id="bb00e-120">DelayActivityTemplate プロジェクトを右クリックして**ソリューション エクスプ ローラー**選択**追加**し**新しい項目の**を開くには、 **の新しい項目の追加** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="bb00e-120">Right-click the DelayActivityTemplate project in **Solution Explorer** and choose **Add** and then **New Item** to open the **Add New Item** dialog box.</span></span>  
  
11. <span data-ttu-id="bb00e-121">選択、**クラス**テンプレート、MyDelayTemplate、という名前をクリック**OK**です。</span><span class="sxs-lookup"><span data-stu-id="bb00e-121">Select the **Class** template, name it MyDelayTemplate, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="bb00e-122">MyDelayTemplate.cs ファイルを開き、次のステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="bb00e-122">Open the MyDelayTemplate.cs file and add the following statements.</span></span>  
  
    ```  
    //Namespaces added  
    using System.Activities;  
    using System.Activities.Statements;  
    using System.Activities.Presentation;  
    using System.Windows;  
    ```  
  
13. <span data-ttu-id="bb00e-123">次のコードを使用して、<xref:System.Activities.Presentation.IActivityTemplateFactory> クラスを持つ `MyDelayActivity` を実装します。</span><span class="sxs-lookup"><span data-stu-id="bb00e-123">Implement the <xref:System.Activities.Presentation.IActivityTemplateFactory> with the `MyDelayActivity` class with the following code.</span></span> <span data-ttu-id="bb00e-124">これにより、10 秒間の遅延が構成されます。</span><span class="sxs-lookup"><span data-stu-id="bb00e-124">This configures the delay to have a duration of 10 seconds.</span></span>  
  
    ```  
    public sealed class MyDelayActivity : IActivityTemplateFactory  
    {  
        public Activity Create(System.Windows.DependencyObject target)  
        {  
            return new System.Activities.Statements.Delay  
            {  
                DisplayName = "DelayActivityTemplate",  
                Duration = new TimeSpan(0, 0, 10)  
  
            };  
        }  
    }  
    ```  
  
14. <span data-ttu-id="bb00e-125">選択**ソリューションのビルド**から、**ビルド**メニュー DelayActivityTemplate.dll ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="bb00e-125">Select **Build Solution** from the **Build** menu to generate the DelayActivityTemplate.dll file.</span></span>  
  
### <a name="to-make-the-template-available-in-a-workflow-designer"></a><span data-ttu-id="bb00e-126">ワークフロー デザイナーでテンプレートを利用できるようにするには</span><span class="sxs-lookup"><span data-stu-id="bb00e-126">To make the template available in a Workflow Designer</span></span>  
  
1.  <span data-ttu-id="bb00e-127">DelayActivityTemplate ソリューションを右クリックして**ソリューション エクスプ ローラー**選択**追加**し**新しいプロジェクト**を開くには、 **の新しいプロジェクトの追加**  ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="bb00e-127">Right-click the DelayActivityTemplate solution in **Solution Explorer** and choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="bb00e-128">選択、**ワークフロー コンソール アプリケーション**テンプレート、名前を付けます`CustomActivityTemplateApp`、順にクリック**[ok]**です。</span><span class="sxs-lookup"><span data-stu-id="bb00e-128">Select the **Workflow Console Application** template, name it `CustomActivityTemplateApp`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="bb00e-129">CustomActivityTemplateApp プロジェクトの [参照設定] ディレクトリを右クリックして**ソリューション エクスプ ローラー**選択**参照の追加**を開くには、**参照の追加**ダイアログボックスです。</span><span class="sxs-lookup"><span data-stu-id="bb00e-129">Right-click the References directory of the CustomActivityTemplateApp project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>  
  
4.  <span data-ttu-id="bb00e-130">移動して、**プロジェクト**タブおよび選択**DelayActivityTemplate**から、**プロジェクト名**クリックして左の列**OK**を追加する、最初の手順で作成した DelayActivityTemplate.dll ファイルへの参照します。</span><span class="sxs-lookup"><span data-stu-id="bb00e-130">Go to the **Projects** tab and select **DelayActivityTemplate** from the **Project Name** column on the left and click **OK** to add a reference to the DelayActivityTemplate.dll file that you created in the first procedure.</span></span>  
  
5.  <span data-ttu-id="bb00e-131">CustomActivityTemplateApp プロジェクトを右クリックして**ソリューション エクスプ ローラー**選択**ビルド**アプリケーションをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="bb00e-131">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Build** to compile the application.</span></span>  
  
6.  <span data-ttu-id="bb00e-132">CustomActivityTemplateApp プロジェクトを右クリックして**ソリューション エクスプ ローラー**選択**スタートアップ プロジェクトとして設定**です。</span><span class="sxs-lookup"><span data-stu-id="bb00e-132">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Set as Startup Project**.</span></span>  
  
7.  <span data-ttu-id="bb00e-133">選択**デバッグなしで開始**から、**デバッグ**メニューとキーを押して任意のキーを cmd.exe ウィンドウから入力を求められたらを続行します。</span><span class="sxs-lookup"><span data-stu-id="bb00e-133">Select **Start Without Debugging** from the **Debug** menu and press any key to continue when prompted from the cmd.exe window.</span></span>  
  
8.  <span data-ttu-id="bb00e-134">Workflow1.xaml ファイルを開き、開き、**ツールボックス**です。</span><span class="sxs-lookup"><span data-stu-id="bb00e-134">Open the Workflow1.xaml file and open the **Toolbox**.</span></span>  
  
9. <span data-ttu-id="bb00e-135">検索、 **MyDelayActivity**でテンプレート、 **DelayActivityTemplate**カテゴリ。</span><span class="sxs-lookup"><span data-stu-id="bb00e-135">Locate the **MyDelayActivity** template in the **DelayActivityTemplate** category.</span></span> <span data-ttu-id="bb00e-136">デザイン サーフェイスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="bb00e-136">Drag it onto the design surface.</span></span> <span data-ttu-id="bb00e-137">ことを確認、**プロパティ**ウィンドウを`Duration`プロパティが 10 秒に設定されています。</span><span class="sxs-lookup"><span data-stu-id="bb00e-137">Confirm in the **Properties** window that the `Duration` property has been set to 10 seconds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb00e-138">例</span><span class="sxs-lookup"><span data-stu-id="bb00e-138">Example</span></span>  
 <span data-ttu-id="bb00e-139">MyDelayActivity.cs ファイルには次のコードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bb00e-139">The MyDelayActivity.cs file should contain the following code.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
//Namespaces added  
using System.Activities;  
using System.Activities.Statements;  
using System.Activities.Presentation;  
using System.Windows;  
  
namespace DelayActivityTemplate  
{  
    public sealed class MyDelayActivity : IActivityTemplateFactory  
    {  
        public Activity Create(System.Windows.DependencyObject target)  
        {  
            return new System.Activities.Statements.Delay  
            {  
                DisplayName = "DelayActivityTemplate",  
                Duration = new TimeSpan(0, 0, 10)  
  
            };  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="bb00e-140">参照</span><span class="sxs-lookup"><span data-stu-id="bb00e-140">See Also</span></span>  
 <xref:System.Activities.Presentation.IActivityTemplateFactory>  
 [<span data-ttu-id="bb00e-141">ワークフロー デザイン操作のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="bb00e-141">Customizing the Workflow Design Experience</span></span>](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)
