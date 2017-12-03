---
title: "手続き型アクティビティの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c67f739-3878-48ad-806c-b2ce0d6733a0
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2d0aeafeaf78e25f612ededf2f6a15061ec280a2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="using-procedural-activities"></a><span data-ttu-id="971d7-102">手続き型アクティビティの使用</span><span class="sxs-lookup"><span data-stu-id="971d7-102">Using Procedural Activities</span></span>
<span data-ttu-id="971d7-103">このサンプルでは、<xref:System.Activities.Statements.Sequence>、<xref:System.Activities.Statements.Assign>、<xref:System.Activities.Statements.If>、<xref:System.Activities.Statements.While>、<xref:System.Activities.Statements.Switch%601>、<xref:System.Activities.Statements.TryCatch>、および <xref:System.Activities.Statements.WriteLine> の各アクティビティを使用して推測ゲームを実装します。</span><span class="sxs-lookup"><span data-stu-id="971d7-103">The sample uses the <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Assign>, <xref:System.Activities.Statements.If>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.Switch%601>, <xref:System.Activities.Statements.TryCatch>, and <xref:System.Activities.Statements.WriteLine> activities to implement a guessing game.</span></span> <span data-ttu-id="971d7-104">推測ゲームではランダムな数値が選択され、プレーヤーはその数値を推測する必要があります。</span><span class="sxs-lookup"><span data-stu-id="971d7-104">The guessing game selects a random number and the player has to guess that number.</span></span> <span data-ttu-id="971d7-105">プレーヤーが送信した推測が間違っていると、ワークフローは、その値が正解よりも上か下かを示すヒントを提供します。</span><span class="sxs-lookup"><span data-stu-id="971d7-105">When the player submits an incorrect guess, the workflow provides a hint whether to guess higher or lower.</span></span> <span data-ttu-id="971d7-106">プレーヤーが 7 回未満で数値を推測できた場合は、特別な祝福のメッセージがユーザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="971d7-106">If the player guesses the number in less than 7 attempts, a special congratulations is displayed to the user.</span></span>  
  
## <a name="custom-activities-in-this-sample"></a><span data-ttu-id="971d7-107">このサンプルのカスタム アクティビティ</span><span class="sxs-lookup"><span data-stu-id="971d7-107">Custom Activities in this Sample</span></span>  
  
### <a name="readline"></a><span data-ttu-id="971d7-108">ReadLine</span><span class="sxs-lookup"><span data-stu-id="971d7-108">ReadLine</span></span>  
 <span data-ttu-id="971d7-109">コンソールからテキスト行を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="971d7-109">Reads a line of text from the console.</span></span> <span data-ttu-id="971d7-110">このアクティビティは <xref:System.Activities.NativeActivity> クラスから派生し、行が読み取られるときにコンソール アプリケーションによって再開されるブックマークを作成します。</span><span class="sxs-lookup"><span data-stu-id="971d7-110">This activity derives from the <xref:System.Activities.NativeActivity> class and creates a bookmark that is resumed by the console application when a line is read.</span></span>  
  
### <a name="promptint"></a><span data-ttu-id="971d7-111">PromptInt</span><span class="sxs-lookup"><span data-stu-id="971d7-111">PromptInt</span></span>  
 <span data-ttu-id="971d7-112">ユーザーに数値の入力を求めるメッセージを表示し、その数値をコンソール ウィンドウから読み取ります。</span><span class="sxs-lookup"><span data-stu-id="971d7-112">Prompts the user to type in a number and then reads it from a console window.</span></span> <span data-ttu-id="971d7-113">このアクティビティは <xref:System.Activities.Activity%601> から派生し、<xref:System.Activities.Statements.WriteLine> アクティビティと `ReadLine` アクティビティを使用します。</span><span class="sxs-lookup"><span data-stu-id="971d7-113">The activity derives from <xref:System.Activities.Activity%601> and uses the <xref:System.Activities.Statements.WriteLine> and `ReadLine` activities.</span></span>  
  
##### <a name="to-use-this-sample"></a><span data-ttu-id="971d7-114">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="971d7-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="971d7-115">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、GuessingGame.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="971d7-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the GuessingGame.sln solution file.</span></span>  
  
2.  <span data-ttu-id="971d7-116">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="971d7-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="971d7-117">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="971d7-117">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="971d7-118">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="971d7-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="971d7-119">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="971d7-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="971d7-120">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="971d7-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="971d7-121">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="971d7-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Procedurals`