---
title: "/subsystemversion (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
caps.latest.revision: 9
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
ms.openlocfilehash: efeade3fcde18f02b3a760adc50d3555df6c9ed7
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="subsystemversion-visual-basic"></a><span data-ttu-id="a4e82-102">/subsystemversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4e82-102">/subsystemversion (Visual Basic)</span></span>
<span data-ttu-id="a4e82-103">生成された実行可能ファイルを実行できる実行可能ファイルを実行できる Windows のバージョンを決定できるサブシステムの最小バージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="a4e82-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="a4e82-104">ほとんどの場合、このオプションは、実行可能ファイルが古いバージョンの Windows では使用できない特定のセキュリティ機能を活用できます。</span><span class="sxs-lookup"><span data-stu-id="a4e82-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4e82-105">自体サブシステムを指定するには、使用、 [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md)コンパイラ オプション。</span><span class="sxs-lookup"><span data-stu-id="a4e82-105">To specify the subsystem itself, use the [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) compiler option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4e82-106">構文</span><span class="sxs-lookup"><span data-stu-id="a4e82-106">Syntax</span></span>  
  
```vb  
/subsystemversion:major.minor  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4e82-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a4e82-107">Parameters</span></span>  
 `major.minor`  
 <span data-ttu-id="a4e82-108">最小値では、メジャーおよびマイナー バージョンのドット付き表記で表される、サブシステムのバージョンが必要です。</span><span class="sxs-lookup"><span data-stu-id="a4e82-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="a4e82-109">たとえば、オペレーティング システムである Windows 7 より古い場合は 6.01 にこのオプションの値を設定する場合は、このトピックの後半の表に示すようにアプリケーションを実行できないことを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a4e82-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="a4e82-110">値を指定する必要があります`major`と`minor`整数値として。</span><span class="sxs-lookup"><span data-stu-id="a4e82-110">You must specify the values for `major` and `minor` as integers.</span></span>  
  
 <span data-ttu-id="a4e82-111">先頭ゼロで、`minor`バージョンは、バージョンを変更しないが、後続のゼロの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="a4e82-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="a4e82-112">たとえば、6.1 と 6.01、同じバージョンを参照してください。 6.10 が別のバージョン。</span><span class="sxs-lookup"><span data-stu-id="a4e82-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="a4e82-113">混乱を避けるためには&2; 桁とマイナー バージョンを表現することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a4e82-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4e82-114">コメント</span><span class="sxs-lookup"><span data-stu-id="a4e82-114">Remarks</span></span>  
 <span data-ttu-id="a4e82-115">次の表は、Windows の一般的なサブシステムのバージョンを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a4e82-115">The following table lists common subsystem versions of Windows.</span></span>  
  
|<span data-ttu-id="a4e82-116">Windows のバージョン</span><span class="sxs-lookup"><span data-stu-id="a4e82-116">Windows version</span></span>|<span data-ttu-id="a4e82-117">サブシステムのバージョン</span><span class="sxs-lookup"><span data-stu-id="a4e82-117">Subsystem version</span></span>|  
|---------------------|-----------------------|  
|<span data-ttu-id="a4e82-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="a4e82-118">Windows 2000</span></span>|<span data-ttu-id="a4e82-119">5.00</span><span class="sxs-lookup"><span data-stu-id="a4e82-119">5.00</span></span>|  
|<span data-ttu-id="a4e82-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="a4e82-120">Windows XP</span></span>|<span data-ttu-id="a4e82-121">5.01</span><span class="sxs-lookup"><span data-stu-id="a4e82-121">5.01</span></span>|  
|<span data-ttu-id="a4e82-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="a4e82-122">Windows Server 2003</span></span>|<span data-ttu-id="a4e82-123">5.02</span><span class="sxs-lookup"><span data-stu-id="a4e82-123">5.02</span></span>|  
|<span data-ttu-id="a4e82-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="a4e82-124">Windows Vista</span></span>|<span data-ttu-id="a4e82-125">6.00</span><span class="sxs-lookup"><span data-stu-id="a4e82-125">6.00</span></span>|  
|<span data-ttu-id="a4e82-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="a4e82-126">Windows 7</span></span>|<span data-ttu-id="a4e82-127">6.01</span><span class="sxs-lookup"><span data-stu-id="a4e82-127">6.01</span></span>|  
|<span data-ttu-id="a4e82-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="a4e82-128">Windows Server 2008</span></span>|<span data-ttu-id="a4e82-129">6.01</span><span class="sxs-lookup"><span data-stu-id="a4e82-129">6.01</span></span>|  
|[!INCLUDE[win8](../../../csharp/language-reference/compiler-options/includes/win8_md.md)]|<span data-ttu-id="a4e82-130">6.02</span><span class="sxs-lookup"><span data-stu-id="a4e82-130">6.02</span></span>|  
  
## <a name="default-values"></a><span data-ttu-id="a4e82-131">既定の値</span><span class="sxs-lookup"><span data-stu-id="a4e82-131">Default values</span></span>  
 <span data-ttu-id="a4e82-132">既定値、 **/subsystemversion**コンパイラ オプションは、以下の条件に依存します。</span><span class="sxs-lookup"><span data-stu-id="a4e82-132">The default value of the **/subsystemversion** compiler option depends on the conditions in the following list:</span></span>  
  
-   <span data-ttu-id="a4e82-133">既定値は次の一覧で任意のコンパイラ オプションが設定されている場合は 6.02、します。</span><span class="sxs-lookup"><span data-stu-id="a4e82-133">The default value is 6.02 if any compiler option in the following list is set:</span></span>  
  
    -   [<span data-ttu-id="a4e82-134">/target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="a4e82-134">/target:appcontainerexe</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [<span data-ttu-id="a4e82-135">/target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="a4e82-135">/target:winmdobj</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [<span data-ttu-id="a4e82-136">/platform:arm</span><span class="sxs-lookup"><span data-stu-id="a4e82-136">/platform:arm</span></span>](../../../visual-basic/reference/command-line-compiler/platform.md)  
  
-   <span data-ttu-id="a4e82-137">MSBuild を使用している場合、既定値は 6.00 は、対象とする[!INCLUDE[net_v45](../../../csharp/language-reference/compiler-options/includes/net_v45_md.md)]、この一覧の前に指定したコンパイラ オプションのいずれかを設定していないとします。</span><span class="sxs-lookup"><span data-stu-id="a4e82-137">The default value is 6.00 if you're using MSBuild, you're targeting [!INCLUDE[net_v45](../../../csharp/language-reference/compiler-options/includes/net_v45_md.md)], and you haven't set any of the compiler options that were specified earlier in this list.</span></span>  
  
-   <span data-ttu-id="a4e82-138">既定値は、上記の条件の [なし] が true の場合、4.00 です。</span><span class="sxs-lookup"><span data-stu-id="a4e82-138">The default value is 4.00 if none of the previous conditions is true.</span></span>  
  
## <a name="setting-this-option"></a><span data-ttu-id="a4e82-139">このオプションを設定する</span><span class="sxs-lookup"><span data-stu-id="a4e82-139">Setting this option</span></span>  
 <span data-ttu-id="a4e82-140">設定する、 **/subsystemversion**コンパイラ オプション Visual Studio には、.vbproj ファイルを開くし、の値を指定する必要があります、 `SubsystemVersion` MSBuild XML 内のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="a4e82-140">To set the **/subsystemversion** compiler option in Visual Studio, you must open the .vbproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="a4e82-141">Visual Studio IDE では、このオプションを設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="a4e82-141">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="a4e82-142">詳細については、このトピックの「既定値"を参照してください。 または[MSBuild プロジェクトの共通プロパティ](https://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties)します。</span><span class="sxs-lookup"><span data-stu-id="a4e82-142">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](https://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties).</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="a4e82-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="a4e82-143">See Also</span></span>  
[<span data-ttu-id="a4e82-144">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="a4e82-144">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)

[<span data-ttu-id="a4e82-145">MSBuild プロパティ</span><span class="sxs-lookup"><span data-stu-id="a4e82-145">MSBuild Properties</span></span>](https://docs.microsoft.com/visualstudio/msbuild/msbuild-properties)

