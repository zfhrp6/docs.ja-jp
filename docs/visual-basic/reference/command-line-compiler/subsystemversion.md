---
title: /subsystemversion (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8330896f890febc4d9f8627715fdd55a8f341f0c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="subsystemversion-visual-basic"></a><span data-ttu-id="65e49-102">/subsystemversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65e49-102">/subsystemversion (Visual Basic)</span></span>
<span data-ttu-id="65e49-103">生成された実行可能ファイルが動作できるサブシステムの最小バージョンを指定します。これにより、実行可能ファイルが動作できる Windows のバージョンが決まります。</span><span class="sxs-lookup"><span data-stu-id="65e49-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="65e49-104">通常、このオプションを指定することで、実行可能ファイルが、Windows の以前のバージョンでは使用できない特定のセキュリティ機能を利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="65e49-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65e49-105">サブシステム自体を指定するには、[/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) のコンパイラ オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="65e49-105">To specify the subsystem itself, use the [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) compiler option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65e49-106">構文</span><span class="sxs-lookup"><span data-stu-id="65e49-106">Syntax</span></span>  
  
```vb  
/subsystemversion:major.minor  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65e49-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="65e49-107">Parameters</span></span>  
 `major.minor`  
 <span data-ttu-id="65e49-108">サブシステムに必要な最小バージョン。メジャー バージョンおよびマイナー バージョンのドット表記で表されます。</span><span class="sxs-lookup"><span data-stu-id="65e49-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="65e49-109">たとえば、このオプションの値を 6.01 に設定すると、Windows 7 より古いオペレーティング システムではアプリケーションを実行できないように指定できます (このトピックの以下の表を参照)。</span><span class="sxs-lookup"><span data-stu-id="65e49-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="65e49-110">`major` と `minor` の値を整数で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65e49-110">You must specify the values for `major` and `minor` as integers.</span></span>  
  
 <span data-ttu-id="65e49-111">`minor` バージョンでは、前に配置されるゼロによってバージョンが変更されることはありませんが、後ろにゼロが付くとバージョンが変わります。</span><span class="sxs-lookup"><span data-stu-id="65e49-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="65e49-112">たとえば、6.1 と 6.01 は同じバージョンを示しますが、6.10 は異なるバージョンを示します。</span><span class="sxs-lookup"><span data-stu-id="65e49-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="65e49-113">混乱を避けるため、マイナー バージョンには 2 桁の数値を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="65e49-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65e49-114">コメント</span><span class="sxs-lookup"><span data-stu-id="65e49-114">Remarks</span></span>  
 <span data-ttu-id="65e49-115">次の表は、Windows の一般的なサブシステムのバージョンを示しています。</span><span class="sxs-lookup"><span data-stu-id="65e49-115">The following table lists common subsystem versions of Windows.</span></span>  
  
|<span data-ttu-id="65e49-116">Windows のバージョン</span><span class="sxs-lookup"><span data-stu-id="65e49-116">Windows version</span></span>|<span data-ttu-id="65e49-117">サブシステムのバージョン</span><span class="sxs-lookup"><span data-stu-id="65e49-117">Subsystem version</span></span>|  
|---------------------|-----------------------|  
|<span data-ttu-id="65e49-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="65e49-118">Windows 2000</span></span>|<span data-ttu-id="65e49-119">5.00</span><span class="sxs-lookup"><span data-stu-id="65e49-119">5.00</span></span>|  
|<span data-ttu-id="65e49-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="65e49-120">Windows XP</span></span>|<span data-ttu-id="65e49-121">5.01</span><span class="sxs-lookup"><span data-stu-id="65e49-121">5.01</span></span>|  
|<span data-ttu-id="65e49-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="65e49-122">Windows Server 2003</span></span>|<span data-ttu-id="65e49-123">5.02</span><span class="sxs-lookup"><span data-stu-id="65e49-123">5.02</span></span>|  
|<span data-ttu-id="65e49-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="65e49-124">Windows Vista</span></span>|<span data-ttu-id="65e49-125">6.00</span><span class="sxs-lookup"><span data-stu-id="65e49-125">6.00</span></span>|  
|<span data-ttu-id="65e49-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="65e49-126">Windows 7</span></span>|<span data-ttu-id="65e49-127">6.01</span><span class="sxs-lookup"><span data-stu-id="65e49-127">6.01</span></span>|  
|<span data-ttu-id="65e49-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="65e49-128">Windows Server 2008</span></span>|<span data-ttu-id="65e49-129">6.01</span><span class="sxs-lookup"><span data-stu-id="65e49-129">6.01</span></span>|  
|[!INCLUDE[win8](~/includes/win8-md.md)]|<span data-ttu-id="65e49-130">6.02</span><span class="sxs-lookup"><span data-stu-id="65e49-130">6.02</span></span>|  
  
## <a name="default-values"></a><span data-ttu-id="65e49-131">既定の値</span><span class="sxs-lookup"><span data-stu-id="65e49-131">Default values</span></span>  
 <span data-ttu-id="65e49-132">**/subsystemversion** コンパイラ オプションの既定値は条件によって異なります。その条件を次に示します。</span><span class="sxs-lookup"><span data-stu-id="65e49-132">The default value of the **/subsystemversion** compiler option depends on the conditions in the following list:</span></span>  
  
-   <span data-ttu-id="65e49-133">次のコンパイラ オプションのいずれかが設定されている場合、既定値は 6.02 です。</span><span class="sxs-lookup"><span data-stu-id="65e49-133">The default value is 6.02 if any compiler option in the following list is set:</span></span>  
  
    -   [<span data-ttu-id="65e49-134">/target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="65e49-134">/target:appcontainerexe</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [<span data-ttu-id="65e49-135">/target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="65e49-135">/target:winmdobj</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [<span data-ttu-id="65e49-136">/platform:arm</span><span class="sxs-lookup"><span data-stu-id="65e49-136">/platform:arm</span></span>](../../../visual-basic/reference/command-line-compiler/platform.md)  
  
-   <span data-ttu-id="65e49-137">MSBuild を使用しており、[!INCLUDE[net_v45](~/includes/net-v45-md.md)] が対象で、さらにこの一覧で前に指定したコンパイラ オプションを設定していない場合、既定値は 6.00 です。</span><span class="sxs-lookup"><span data-stu-id="65e49-137">The default value is 6.00 if you're using MSBuild, you're targeting [!INCLUDE[net_v45](~/includes/net-v45-md.md)], and you haven't set any of the compiler options that were specified earlier in this list.</span></span>  
  
-   <span data-ttu-id="65e49-138">上記の条件がどれも当てはまらない場合、既定値は 4.00 です。</span><span class="sxs-lookup"><span data-stu-id="65e49-138">The default value is 4.00 if none of the previous conditions is true.</span></span>  
  
## <a name="setting-this-option"></a><span data-ttu-id="65e49-139">このオプションを設定する</span><span class="sxs-lookup"><span data-stu-id="65e49-139">Setting this option</span></span>  
 <span data-ttu-id="65e49-140">設定する、 **/subsystemversion**コンパイラ オプション Visual Studio で、.vbproj ファイルを開くし、値を指定する必要があります、 `SubsystemVersion` MSBuild XML 内のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="65e49-140">To set the **/subsystemversion** compiler option in Visual Studio, you must open the .vbproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="65e49-141">Visual Studio IDE でこのオプションを設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="65e49-141">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="65e49-142">詳細については、このトピックの「既定値」または「[MSBuild プロジェクトの共通プロパティ](/visualstudio/msbuild/common-msbuild-project-properties)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65e49-142">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="65e49-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="65e49-143">See Also</span></span>  
[<span data-ttu-id="65e49-144">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="65e49-144">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)

[<span data-ttu-id="65e49-145">MSBuild プロパティ</span><span class="sxs-lookup"><span data-stu-id="65e49-145">MSBuild Properties</span></span>](/visualstudio/msbuild/msbuild-properties)
