---
title: ポリシーを使用した注文処理
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 66833724-dc36-4fad-86b0-59ffeaa3ba6a
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f99db44a636a5255990f734d34266b3b2e4a678b
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="order-processing-with-policy"></a><span data-ttu-id="eb12e-102">ポリシーを使用した注文処理</span><span class="sxs-lookup"><span data-stu-id="eb12e-102">Order Processing with Policy</span></span>
<span data-ttu-id="eb12e-103">注文処理ポリシー サンプルでは、Windows WF (Workflow Foundation) の [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] に導入された重要な機能の一部を示しています。</span><span class="sxs-lookup"><span data-stu-id="eb12e-103">The Order Processing Policy sample demonstrates some of the key features introduced in the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] of the Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="eb12e-104">次の機能が WF ルール エンジンに新しく追加されました。</span><span class="sxs-lookup"><span data-stu-id="eb12e-104">The following functionality is new for the WF rules engine:</span></span>  
  
-   <span data-ttu-id="eb12e-105">演算子のオーバーロードのサポート。</span><span class="sxs-lookup"><span data-stu-id="eb12e-105">Support for operator overloading.</span></span>  
  
-   <span data-ttu-id="eb12e-106">`new` 演算子のサポート。これにより、WF ルールから新しいオブジェクトおよび配列を作成できます。</span><span class="sxs-lookup"><span data-stu-id="eb12e-106">Support for the `new` operator, allowing users to create new objects and arrays from WF rules.</span></span>  
  
-   <span data-ttu-id="eb12e-107">拡張メソッドのサポート。これにより、C# のコーディング スタイルとの互換性を持つ拡張メソッドのWF ルールからの呼び出しが容易かつ便利になります。</span><span class="sxs-lookup"><span data-stu-id="eb12e-107">Support for extension methods to make the user experience in calling extension methods from WF rules compatible with C# coding styles.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb12e-108">このサンプルでは、ビルドおよび実行のために [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] がインストールされていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="eb12e-108">This sample requires that [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] is installed to build and run.</span></span> [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]<span data-ttu-id="eb12e-109"> ではプロジェクトとソリューション ファイルを開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb12e-109"> is required to open the project and solution files.</span></span>  
  
 <span data-ttu-id="eb12e-110">このサンプルでは、使用できるアイテムの番号付きリストと郵便番号で構成される顧客の注文を入力する、`OrderProcessingPolicy` プロジェクトを示します。</span><span class="sxs-lookup"><span data-stu-id="eb12e-110">The sample demonstrates an `OrderProcessingPolicy` project in which a customer order, which consists of a numbered list of available items and a zip code, is entered.</span></span> <span data-ttu-id="eb12e-111">両方の入力が正しい場合は、注文が正常に処理されますが、正しくない場合は、ポリシーによってエラー オブジェクトが作成され、オーバーロードされた `+` 演算子と定義済みの拡張メソッドによって、ユーザーにエラーが通知されます。</span><span class="sxs-lookup"><span data-stu-id="eb12e-111">The order is processed successfully if both entries are correct; otherwise, the policy creates error objects, utilizing an overloaded `+` operator and a predefined extension method to inform the user of the errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb12e-112">拡張メソッドの詳細については、次を参照してください。 [c# バージョン 3.0 の仕様](http://go.microsoft.com/fwlink/?LinkId=95402)です。</span><span class="sxs-lookup"><span data-stu-id="eb12e-112">For more information about extension methods, see [C# Version 3.0 Specification](http://go.microsoft.com/fwlink/?LinkId=95402).</span></span>  
  
 <span data-ttu-id="eb12e-113">サンプルは、以下のプロジェクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="eb12e-113">The sample is comprised of the following projects:</span></span>  
  
-   `OrderErrorLibrary`  
  
     <span data-ttu-id="eb12e-114">`OrderErrorLibrary` は、`OrderError` クラスおよび `OrderErrorCollection` クラスを定義するクラス ライブラリです。</span><span class="sxs-lookup"><span data-stu-id="eb12e-114">The `OrderErrorLibrary` is a class library that defines `OrderError` and `OrderErrorCollection` classes.</span></span> <span data-ttu-id="eb12e-115">`OrderError` インスタンスは、無効な入力が行われたときに作成されます。</span><span class="sxs-lookup"><span data-stu-id="eb12e-115">An `OrderError` instance is created when an invalid input is entered.</span></span> <span data-ttu-id="eb12e-116">ライブラリには、`OrderErrorCollection` 内のすべての `ErrorText` オブジェクトの `OrderError` プロパティを出力する `OrderErrorCollection` クラスの拡張メソッドも用意されています。</span><span class="sxs-lookup"><span data-stu-id="eb12e-116">The library also provides an extension method on the `OrderErrorCollection` class that outputs the `ErrorText` property on all `OrderError` objects in the `OrderErrorCollection`.</span></span>  
  
-   `OrderProcessingPolicy`  
  
     <span data-ttu-id="eb12e-117">`OrderProcessingPolicy` プロジェクトは、1 つの `PolicyFromFile` アクティビティを定義する WF コンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="eb12e-117">The `OrderProcessingPolicy` project is a WF console application that defines a single `PolicyFromFile` activity.</span></span> <span data-ttu-id="eb12e-118">このアクティビティには、以下のルールがあります。</span><span class="sxs-lookup"><span data-stu-id="eb12e-118">The activity has the following rules:</span></span>  
  
    -   `invalidItemNum`  
  
         <span data-ttu-id="eb12e-119">このルールでは、アイテム番号が 1 ～ 6 の範囲内かどうかが検証されます。</span><span class="sxs-lookup"><span data-stu-id="eb12e-119">This rule validates that the item number is between 1 and 6, inclusive.</span></span> <span data-ttu-id="eb12e-120">アイテム番号が有効範囲内の場合は、コンソールへの出力を除き、処理は何も行われません。</span><span class="sxs-lookup"><span data-stu-id="eb12e-120">If the item number is within the valid range, the rule does nothing (other than printing to the console).</span></span> <span data-ttu-id="eb12e-121">アイテム番号が 1 ～ 6 の範囲外の場合は、`invalidItemNum` ルールによって以下の処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="eb12e-121">If the item number is not between 1 and 6, the `invalidItemNum` rule does the following:</span></span>  
  
        1.  <span data-ttu-id="eb12e-122">新しい `OrderError` オブジェクトを作成し、入力されたアイテム番号をこのオブジェクトに渡して、このオブジェクトの `ErrorText` プロパティおよび `CustomerName` プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="eb12e-122">Creates a new `OrderError` object, passing it the item number entered, and sets the `ErrorText` and `CustomerName` properties on the object.</span></span>  
  
        2.  <span data-ttu-id="eb12e-123">`invalidItemNumErrorCollection` オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="eb12e-123">Creates an `invalidItemNumErrorCollection` object.</span></span>  
  
        3.  <span data-ttu-id="eb12e-124">新しく作成した `OrderError` インスタンスを `invalidItemNumErrorCollection` に追加します。</span><span class="sxs-lookup"><span data-stu-id="eb12e-124">Adds the newly-created `OrderError` instance to the `invalidItemNumErrorCollection`.</span></span>  
  
         <span data-ttu-id="eb12e-125">これは、ルール内でオブジェクトのインスタンスを作成できる `new` 演算子がサポートされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="eb12e-125">This demonstrates support for the `new` operator, with which you can instantiate objects inside rules.</span></span>  
  
    -   `invalidZip`  
  
         <span data-ttu-id="eb12e-126">このルールでは、郵便番号が 5 桁で、600 ～ 99998 の範囲内にあるかどうかを検証します。</span><span class="sxs-lookup"><span data-stu-id="eb12e-126">This rule validates that the zip code has 5 digits, and is within the range 600 to 99998.</span></span> <span data-ttu-id="eb12e-127">郵便番号が有効範囲内の場合は、コンソールへの出力を除き、処理は何も行われません。</span><span class="sxs-lookup"><span data-stu-id="eb12e-127">If the zip code is within the valid range, the rule does nothing (other than printing to the console).</span></span> <span data-ttu-id="eb12e-128">郵便番号が 5 桁よりも少ないか、郵便番号が 00600 ～ 99998 の範囲外の場合は、`invalidZip` ルールによって以下の処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="eb12e-128">If the length of the zip code is less than 5, or the zip code is not between 00600 and 99998, the `invalidZip` rule does the following:</span></span>  
  
        1.  <span data-ttu-id="eb12e-129">`OrderError` オブジェクトを作成し、入力された郵便番号をこのオブジェクトに渡して、このオブジェクトの `ErrorText` プロパティおよび `CustomerName` プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="eb12e-129">Creates an `OrderError` object, passing it the zip code entered, and sets the `ErrorText` and `CustomerName` properties on the object.</span></span>  
  
        2.  <span data-ttu-id="eb12e-130">`invalidZipCodeErrorCollection` オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="eb12e-130">Creates an `invalidZipCodeErrorCollection` object.</span></span>  
  
        3.  <span data-ttu-id="eb12e-131">新しく作成した `OrderError` インスタンスを、新しく作成した `invalidZipCodeErrorCollection` に追加します。</span><span class="sxs-lookup"><span data-stu-id="eb12e-131">Adds the newly-created `OrderError` instance to the newly-created `invalidZipCodeErrorCollection`.</span></span>  
  
         <span data-ttu-id="eb12e-132">このルールで、`new` 演算子のサポートが再度実現され、ルール内でのオブジェクトのインスタンスの作成が可能となります。</span><span class="sxs-lookup"><span data-stu-id="eb12e-132">This rule again demonstrates support for the `new` operator, which allows you to instantiate objects inside rules.</span></span>  
  
    -   `displayErrors`  
  
         <span data-ttu-id="eb12e-133">このルールでは、上記の 2 つの `OrderErrorCollection` オブジェクト、`invalidItemNumErrorCollection` および `invalidIZipCodeErrorCollection` の 2 つのルールによって追加されたエラーがあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="eb12e-133">This rule checks to see if there were any errors added by the previous two rules in the two `OrderErrorCollection` objects `invalidItemNumErrorCollection` and `invalidIZipCodeErrorCollection`.</span></span> <span data-ttu-id="eb12e-134">エラーがある場合 (`invalidItemNumErrorCollection` または `invalidZipCodeErrorCollection`が `null` ではない場合)、このルールによって以下の処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="eb12e-134">If there were errors (either `invalidItemNumErrorCollection` or `invalidZipCodeErrorCollection` is not `null`), the rule does the following:</span></span>  
  
        1.  <span data-ttu-id="eb12e-135">呼び出し、オーバー ロードされた`+`の内容をコピーする演算子`invalidItemNumErrorCollection`と`invalidZipCodeErrorCollection`を`invalidOrdersCollection``OrderErrorCollection`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="eb12e-135">Calls the overloaded `+` operator to copy the contents of `invalidItemNumErrorCollection` and `invalidZipCodeErrorCollection` to an `invalidOrdersCollection``OrderErrorCollection` instance.</span></span>  
  
        2.  <span data-ttu-id="eb12e-136">`PrintOrderErrors` の `invalidOrdersCollection` 拡張メソッドを呼び出し、`ErrorText` 内のすべての `orderError` オブジェクトの `invalidOrdersCollection` プロパティを出力します。</span><span class="sxs-lookup"><span data-stu-id="eb12e-136">Calls the `PrintOrderErrors` extension method on `invalidOrdersCollection` and outputs the `ErrorText` property on all `orderError` objects in `invalidOrdersCollection`.</span></span>  
  
 <span data-ttu-id="eb12e-137">`+` のオーバーロードされた `OrderErrorCollection` 演算子は、`OrderErrorCollection` プロジェクトの `OrderErrorLibrary` クラスで定義されています。</span><span class="sxs-lookup"><span data-stu-id="eb12e-137">The overloaded operator `+` on the `OrderErrorCollection` is defined in the `OrderErrorCollection` class, in the `OrderErrorLibrary` project.</span></span> <span data-ttu-id="eb12e-138">この演算子は、2 つの `OrderErrorCollection` オブジェクトを受け取り、1 つの `OrderErrorCollection` オブジェクトに結合します。</span><span class="sxs-lookup"><span data-stu-id="eb12e-138">It takes two `OrderErrorCollection` objects and combines them into one `OrderErrorCollection` object.</span></span>  
  
 <span data-ttu-id="eb12e-139">`PrintOrderErrors` 拡張メソッドも `OrderErrorLibrary` プロジェクトで定義されています。</span><span class="sxs-lookup"><span data-stu-id="eb12e-139">The `PrintOrderErrors` extension method is also defined in the `OrderErrorLibrary` project.</span></span> <span data-ttu-id="eb12e-140">拡張メソッドは C# の新機能であり、開発者は、クラスの派生や元の型の再コンパイルを行わなくても、新しいメソッドを既存の CLR 型のパブリック コントラクトに追加できます。</span><span class="sxs-lookup"><span data-stu-id="eb12e-140">Extension methods are a new C# feature that enables developers to add new methods to the public contract of an existing CLR type, without having to derive a class from it or recompile the original type.</span></span>  
  
 <span data-ttu-id="eb12e-141">サンプルを実行すると、名前、購入するアイテムの番号、および郵便番号の入力が求められます。</span><span class="sxs-lookup"><span data-stu-id="eb12e-141">When you run the sample you are prompted to enter a name, the item number of the item to be purchased, and a zip code.</span></span> <span data-ttu-id="eb12e-142">その後、この情報は、ポリシー アクティビティで定義されているルールによって検証されます。</span><span class="sxs-lookup"><span data-stu-id="eb12e-142">This information is then verified by the rules defined in the policy activity.</span></span> <span data-ttu-id="eb12e-143">このプログラムの出力サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="eb12e-143">The following is sample output from the program.</span></span>  
  
```  
Please enter your name: John  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 1  
  
Please enter your 5-Digit zip code: 98102  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Thank you for your order, it has been processed.  
  
Workflow Completed  
Another Order? (Y/N): y  
  
Please enter your name: Joel  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 8  
  
Please enter your 5-Digit zip code: 0000  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Your order contains the following error(s)  
  
Error: No item number found. Please choose an available item.  
Error: Invalid zip code. Please choose a zip code between 00600 and 99998.  
  
Workflow Completed  
Another Order? (Y/N): n  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="eb12e-144">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="eb12e-144">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="eb12e-145">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で OrderProcessingPolicy.sln プロジェクト ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="eb12e-145">Open the OrderProcessingPolicy.sln project file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="eb12e-146">このソリューションには、`OrderErrorLibrary` および `OrderProcessingPolicy` という 2 つの異なるプロジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="eb12e-146">There are two different projects in the solution: `OrderErrorLibrary` and `OrderProcessingPolicy`.</span></span> <span data-ttu-id="eb12e-147">`OrderProcessingPolicy` プロジェクトでは、`OrderErrorLibrary` プロジェクトで定義されているクラスとメソッドが使用されます。</span><span class="sxs-lookup"><span data-stu-id="eb12e-147">The `OrderProcessingPolicy` project uses classes and methods defined in the `OrderErrorLibrary`.</span></span>  
  
3.  <span data-ttu-id="eb12e-148">すべてのプロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="eb12e-148">Build all projects.</span></span>  
  
4.  <span data-ttu-id="eb12e-149">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb12e-149">Click **Run**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="eb12e-150">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="eb12e-150">The samples may already be installed on your computer.</span></span> <span data-ttu-id="eb12e-151">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="eb12e-151">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="eb12e-152">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="eb12e-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="eb12e-153">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="eb12e-153">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\OrderProcessingPolicy`