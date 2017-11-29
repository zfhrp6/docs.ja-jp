---
title: "型プロバイダーのセキュリティ"
description: "F# で型プロバイダーの信頼の設定を変更する方法を含む型プロバイダーのセキュリティについて説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9c5a8a1f-5a31-490d-83c0-8beabda75c78
ms.openlocfilehash: c8f03ee90d4dce1d3484a9dfe8951d500d509a2b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="type-provider-security"></a><span data-ttu-id="90a68-104">型プロバイダーのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="90a68-104">Type Provider Security</span></span>

<span data-ttu-id="90a68-105">型プロバイダーはアセンブリ (Dll) の f# プロジェクトまたはスクリプトによって参照される外部データ ソースに接続し、f# 型の環境にこの型情報を提示するコードを含むです。</span><span class="sxs-lookup"><span data-stu-id="90a68-105">Type providers are assemblies (DLLs) referenced by your F# project or script that contain code to connect to external data sources and surface this type information to the F# type environment.</span></span> <span data-ttu-id="90a68-106">通常は、コンパイル時し、コードを実行 (または、スクリプトの場合、f# Interactive にコードを送信します)、参照されたアセンブリ内のコードは実行のみ。</span><span class="sxs-lookup"><span data-stu-id="90a68-106">Typically, code in referenced assemblies is only run when you compile and then execute the code (or in the case of a script, send the code to F# Interactive).</span></span> <span data-ttu-id="90a68-107">ただし、型プロバイダー アセンブリは、エディターでコードが参照されるだけで、Visual Studio で実行されます。</span><span class="sxs-lookup"><span data-stu-id="90a68-107">However, a type provider assembly will run inside Visual Studio when the code is merely browsed in the editor.</span></span> <span data-ttu-id="90a68-108">これは、型プロバイダーは、クイック ヒントのツールヒント、IntelliSense 入力候補などのエディターに余分な情報の追加を実行する必要があるために発生します。</span><span class="sxs-lookup"><span data-stu-id="90a68-108">This happens because type providers need to run to add extra information to the editor, such as Quick Info tooltips, IntelliSense completions, and so on.</span></span> <span data-ttu-id="90a68-109">その結果、余分なセキュリティの種類に関する考慮事項プロバイダー アセンブリが、Visual Studio プロセス内に自動的に実行されるためです。</span><span class="sxs-lookup"><span data-stu-id="90a68-109">As a result, there are extra security considerations for type provider assemblies, since they run automatically inside the Visual Studio process.</span></span>


## <a name="security-warning-dialog"></a><span data-ttu-id="90a68-110">セキュリティ警告 ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="90a68-110">Security Warning Dialog</span></span>
<span data-ttu-id="90a68-111">を最初に、特定の型プロバイダー アセンブリを使用する場合、Visual Studio には、を実行する型プロバイダーがあることを警告するセキュリティのダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="90a68-111">When using a particular type provider assembly for the first time, Visual Studio displays a security dialog that warns you that the type provider is about to run.</span></span> <span data-ttu-id="90a68-112">Visual Studio で、型プロバイダーが読み込まれる前に、使用する、この特定のプロバイダーを信頼できるかどうかを決定することができます。</span><span class="sxs-lookup"><span data-stu-id="90a68-112">Before Visual Studio loads the type provider, it gives you the opportunity to decide if you trust this particular provider.</span></span> <span data-ttu-id="90a68-113">型プロバイダーのソースを信頼する場合は、「この型プロバイダーが信頼されます」ですを選択し、</span><span class="sxs-lookup"><span data-stu-id="90a68-113">If you trust the source of the type provider, then select "I trust this type provider."</span></span> <span data-ttu-id="90a68-114">型プロバイダーのソースを信頼していない場合は、「は信頼できないこの型プロバイダーです」を選択し、</span><span class="sxs-lookup"><span data-stu-id="90a68-114">If you do not trust the source of the type provider, then select "I do not trust this type provider."</span></span> <span data-ttu-id="90a68-115">プロバイダーを信頼する、Visual Studio 内で実行し IntelliSense を提供し、機能を構築できます。</span><span class="sxs-lookup"><span data-stu-id="90a68-115">Trusting the provider enables it to run inside Visual Studio and provide IntelliSense and build features.</span></span> <span data-ttu-id="90a68-116">そのコードを実行すると、コンピューターが侵害でした型プロバイダー自体が悪意のある場合は、します。</span><span class="sxs-lookup"><span data-stu-id="90a68-116">But if the type provider itself is malicious, running its code could compromise your machine.</span></span>

<span data-ttu-id="90a68-117">プロジェクトを信頼しないこと、ダイアログ ボックスで選択した型プロバイダーを参照するコードが含まれている場合、コンパイル時に、コンパイラ エラーが報告されます型プロバイダーが信頼されていないことを示すです。</span><span class="sxs-lookup"><span data-stu-id="90a68-117">If your project contains code that references type providers that you chose in the dialog not to trust, then at compile time, the compiler will report an error that indicates that the type provider is untrusted.</span></span> <span data-ttu-id="90a68-118">信頼されていない型プロバイダーに依存する任意の種類は、赤の波線で示されます。</span><span class="sxs-lookup"><span data-stu-id="90a68-118">Any types that are dependent on the untrusted type provider are indicated by red squiggles.</span></span> <span data-ttu-id="90a68-119">コード エディターで参照する安全です。</span><span class="sxs-lookup"><span data-stu-id="90a68-119">It is safe to browse the code in the editor.</span></span>

<span data-ttu-id="90a68-120">を直接 Visual Studio での信頼設定を変更する場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="90a68-120">If you decide to change the trust setting directly in Visual Studio, perform the following steps.</span></span>


#### <a name="to-change-the-trust-settings-for-type-providers"></a><span data-ttu-id="90a68-121">型プロバイダーの信頼の設定を変更するには</span><span class="sxs-lookup"><span data-stu-id="90a68-121">To change the trust settings for type providers</span></span>

1. <span data-ttu-id="90a68-122">`Tools`メニューの `Options`を展開し、`F# Tools`ノード。</span><span class="sxs-lookup"><span data-stu-id="90a68-122">On the `Tools` menu, select `Options`, and expand the `F# Tools` node.</span></span>
<br />

2. <span data-ttu-id="90a68-123">選択`Type Providers`、型プロバイダーの一覧で、信頼すると、型プロバイダーのチェック ボックスをオンおよび信頼できないもののチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="90a68-123">Select `Type Providers`, and in the list of type providers, select the check box for type providers you trust, and clear the check box for those you don't trust.</span></span>
<br />


## <a name="see-also"></a><span data-ttu-id="90a68-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="90a68-124">See Also</span></span>
[<span data-ttu-id="90a68-125">型プロバイダー</span><span class="sxs-lookup"><span data-stu-id="90a68-125">Type Providers</span></span>](index.md)
