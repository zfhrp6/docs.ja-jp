---
title: "Windows 8 での .NET Framework 2.0 の指定"
description: "F# を使用する場合は、古いバージョンの .NET Framework を対象とするについて説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 63989543-95c3-4ab7-81f3-3834a8b15010
ms.openlocfilehash: 2c0191267da5bee7b844c11cdee168ccfb3321c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="targeting-older-versions-of-net"></a><span data-ttu-id="0bb33-104">以前のバージョンの .NET の対象化</span><span class="sxs-lookup"><span data-stu-id="0bb33-104">Targeting Older Versions of .NET</span></span>

> [!NOTE]
<span data-ttu-id="0bb33-105">この記事は、最新の Visual Studio と最新の状態はありません。</span><span class="sxs-lookup"><span data-stu-id="0bb33-105">This article is not up to date with the latest Visual Studio.</span></span>  <span data-ttu-id="0bb33-106">これは更新されます。</span><span class="sxs-lookup"><span data-stu-id="0bb33-106">It will be updated.</span></span>

<span data-ttu-id="0bb33-107">3.0、または 3.5 で、f# のプロジェクトの Windows 8.1 で Visual Studio がインストールされているときに、.NET Framework 2.0 を対象にすると、次のエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0bb33-107">The following error might appear if you try to target the .NET Framework 2.0, 3.0, or 3.5 in an F# project when Visual Studio is installed on Windows 8.1:</span></span> 

```
This project requires the 2.0 F# runtime, but that runtime is not installed.
```

<span data-ttu-id="0bb33-108">このエラーが発生するよう、次の条件の組み合わせにわかっています。</span><span class="sxs-lookup"><span data-stu-id="0bb33-108">This error is known to occur under the following combination of conditions:</span></span>


- <span data-ttu-id="0bb33-109">Windows 8.1 には、Visual Studio をインストールします。</span><span class="sxs-lookup"><span data-stu-id="0bb33-109">You installed Visual Studio on Windows 8.1.</span></span>
<br />

- <span data-ttu-id="0bb33-110">Visual Studio をインストールする前に、.NET Framework 3.5 を有効にしませんでした。</span><span class="sxs-lookup"><span data-stu-id="0bb33-110">You didn’t enable the .NET Framework 3.5 before you installed Visual Studio.</span></span>
<br />

- <span data-ttu-id="0bb33-111">プロジェクトでは、.NET Framework 2.0、3.0、または 3.5 を対象します。</span><span class="sxs-lookup"><span data-stu-id="0bb33-111">Your project targets the .NET Framework 2.0, 3.0, or 3.5.</span></span>
<br />

<span data-ttu-id="0bb33-112">Visual Studio をインストールするときに、インストールされている、.NET Framework のバージョンを検出し、.NET Framework 3.5 がインストールされ有効になっている場合にのみ、f# 2.0 ランタイムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="0bb33-112">When you install Visual Studio, it detects the installed versions of the .NET Framework and installs the F# 2.0 Runtime only if the .NET Framework 3.5 is installed and enabled.</span></span>


## <a name="resolving-the-error"></a><span data-ttu-id="0bb33-113">エラーの解決</span><span class="sxs-lookup"><span data-stu-id="0bb33-113">Resolving the Error</span></span>
<span data-ttu-id="0bb33-114">このエラーを解決するには、いずれかの対象 .NET Framework の新しいバージョンを実行できますしたりできます Windows 8.1 での .NET Framework 3.5 を有効にすると Visual Studio のセットアップ プログラムを実行して、f# 2.0 ランタイムをインストール、**修復**オプション。</span><span class="sxs-lookup"><span data-stu-id="0bb33-114">To resolve this error, you can either target a newer version of the .NET Framework, or you can enable the .NET Framework 3.5 on Windows 8.1 and then install the F# 2.0 runtime by running the setup program for Visual Studio with the **Repair** option.</span></span>


#### <a name="to-enable-the-net-framework-35-on-windows-81"></a><span data-ttu-id="0bb33-115">Windows 8.1 での .NET Framework 3.5 を有効にするには</span><span class="sxs-lookup"><span data-stu-id="0bb33-115">To enable the .NET Framework 3.5 on Windows 8.1</span></span>

1. <span data-ttu-id="0bb33-116">**開始**画面で、開始し、入力**コントロール パネルの **です。</span><span class="sxs-lookup"><span data-stu-id="0bb33-116">On the **Start** screen, start to enter **Control Panel**.</span></span>
<br />  <span data-ttu-id="0bb33-117">その名前を入力すると、**コントロール パネルの **下にあるアイコンが表示されます、**アプリ**見出し。</span><span class="sxs-lookup"><span data-stu-id="0bb33-117">As you enter that name, the **Control Panel** icon appears under the **Apps** heading.</span></span>
<br />

2. <span data-ttu-id="0bb33-118">選択、**コントロール パネル** アイコンを選択、**プログラム** アイコンを選択し、 **Windows の機能のオンまたはオフ**リンクします。</span><span class="sxs-lookup"><span data-stu-id="0bb33-118">Choose the **Control Panel** icon, choose the **Programs** icon, and then choose the **Turn Windows features on or off** link.</span></span>
<br />

3. <span data-ttu-id="0bb33-119">確認して、 **.NET Framework 3.5 (.NET 2.0 および 3.0 を含む)**  チェック ボックスを選択してを選択し、 **OK**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0bb33-119">Make sure that the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box is selected, and then choose the **OK** button.</span></span>
<br />  <span data-ttu-id="0bb33-120">オプションのコンポーネント、.NET Framework の子ノードのチェック ボックスをオンにする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0bb33-120">You don’t need to select the check boxes for any child nodes for optional components of the .NET Framework.</span></span>
<br />  <span data-ttu-id="0bb33-121">.NET Framework 3.5 は、既になっていない場合に有効です。</span><span class="sxs-lookup"><span data-stu-id="0bb33-121">The .NET Framework 3.5 is enabled if it wasn't already.</span></span>
<br />


#### <a name="to-install-the-f-20-runtime"></a><span data-ttu-id="0bb33-122">F# 2.0 ランタイムをインストールするには</span><span class="sxs-lookup"><span data-stu-id="0bb33-122">To install the F# 2.0 runtime</span></span>

1. <span data-ttu-id="0bb33-123">コントロール パネル で、**プログラム**リンクをクリックして、**プログラムと機能**リンクします。</span><span class="sxs-lookup"><span data-stu-id="0bb33-123">In the Control Panel, choose the **Programs** link, and then choose the **Programs and Features** link.</span></span>
<br />

2. <span data-ttu-id="0bb33-124">インストールされているプログラムの一覧をインストールし、Visual Studio のエディションを選択、**変更**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0bb33-124">In the list of installed programs, choose the edition of Visual Studio that you installed, and then choose the **Change** button.</span></span>
<br />

3. <span data-ttu-id="0bb33-125">セットアップが起動したら、選択、**修復**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0bb33-125">After setup starts, choose the **Repair** button.</span></span>
<br />  <span data-ttu-id="0bb33-126">詳細については、次を参照してください。 [Visual Studio のインストール](https://msdn.microsoft.com/library/e2h7fzkw.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="0bb33-126">For more information, see [Installing Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx).</span></span>
<br />
## <a name="see-also"></a><span data-ttu-id="0bb33-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="0bb33-127">See Also</span></span>
[<span data-ttu-id="0bb33-128">Visual F#</span><span class="sxs-lookup"><span data-stu-id="0bb33-128">Visual F#</span></span>](../index.md)
