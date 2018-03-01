---
title: "-win32res (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4c24da8bb745847612d882d00eff7f03dbc60475
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="-win32res-c-compiler-options"></a><span data-ttu-id="4d90f-102">-win32res (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="4d90f-102">-win32res (C# Compiler Options)</span></span>
<span data-ttu-id="4d90f-103">**-win32res** オプションは、Win32 リソースを出力ファイルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="4d90f-103">The **-win32res** option inserts a Win32 resource in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d90f-104">構文</span><span class="sxs-lookup"><span data-stu-id="4d90f-104">Syntax</span></span>  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="4d90f-105">引数</span><span class="sxs-lookup"><span data-stu-id="4d90f-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="4d90f-106">出力ファイルに追加するリソース ファイル。</span><span class="sxs-lookup"><span data-stu-id="4d90f-106">The resource file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d90f-107">コメント</span><span class="sxs-lookup"><span data-stu-id="4d90f-107">Remarks</span></span>  
 <span data-ttu-id="4d90f-108">Win32 リソース ファイルは、[リソース コンパイラ](../../language-reference/compiler-options/resource-compiler-option.md)を使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="4d90f-108">A Win32 resource file can be created with the [Resource Compiler](../../language-reference/compiler-options/resource-compiler-option.md).</span></span> <span data-ttu-id="4d90f-109">リソース コンパイラは、Visual C++ プログラムをコンパイルするときに呼び出されます。 .res ファイルは .rc ファイルから作成されます。</span><span class="sxs-lookup"><span data-stu-id="4d90f-109">The Resource Compiler is invoked when you compile a Visual C++ program; a .res file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="4d90f-110">Win32 リソースは、バージョンまたはビットマップ (アイコン) 情報を格納できます。エクスプローラーでアプリケーションを識別するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="4d90f-110">A Win32 resource can contain version or bitmap (icon) information that would help identify your application in the File Explorer.</span></span> <span data-ttu-id="4d90f-111">**-win32res** を指定しない場合、コンパイラはアセンブリ バージョンに基づいてバージョン情報を生成します。</span><span class="sxs-lookup"><span data-stu-id="4d90f-111">If you do not specify **-win32res**, the compiler will generate version information based on the assembly version.</span></span>  
  
 <span data-ttu-id="4d90f-112">.NET Framework リソース ファイルの [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (参照) または [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (アタッチ) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4d90f-112">See [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (to reference) or [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="4d90f-113">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="4d90f-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="4d90f-114">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="4d90f-114">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="4d90f-115">**[アプリケーション]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d90f-115">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="4d90f-116">**[リソース ファイル]** ボタンをクリックし、コンボ ボックスを利用してファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="4d90f-116">Click on the **Resource File** button and choose a file by using the combo box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d90f-117">例</span><span class="sxs-lookup"><span data-stu-id="4d90f-117">Example</span></span>  
 <span data-ttu-id="4d90f-118">`in.cs` をコンパイルし、Win32 リソース ファイル `rf.res` をアタッチし、`in.exe` を作成します。</span><span class="sxs-lookup"><span data-stu-id="4d90f-118">Compile `in.cs` and attach a Win32 resource file `rf.res` to produce `in.exe`:</span></span>  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d90f-119">参照</span><span class="sxs-lookup"><span data-stu-id="4d90f-119">See Also</span></span>  
 [<span data-ttu-id="4d90f-120">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="4d90f-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="4d90f-121">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="4d90f-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
