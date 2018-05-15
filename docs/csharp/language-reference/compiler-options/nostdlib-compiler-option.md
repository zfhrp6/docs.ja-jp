---
title: -nostdlib (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 1dc0ab70ca28626c4a3f505c13ec1d6f828a4b05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="8622d-102">-nostdlib (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="8622d-102">-nostdlib (C# Compiler Options)</span></span>
<span data-ttu-id="8622d-103">**-nostdlib** は、System 名前空間の全体を定義する mscorlib.dll がインポートされないようにします。</span><span class="sxs-lookup"><span data-stu-id="8622d-103">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8622d-104">構文</span><span class="sxs-lookup"><span data-stu-id="8622d-104">Syntax</span></span>  
  
```console  
-nostdlib[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="8622d-105">コメント</span><span class="sxs-lookup"><span data-stu-id="8622d-105">Remarks</span></span>  
 <span data-ttu-id="8622d-106">独自の System 名前空間およびオブジェクトを定義または作成する場合は、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="8622d-106">Use this option if you want to define or create your own System namespace and objects.</span></span>  
  
 <span data-ttu-id="8622d-107">**-nostdlib** を指定しないと、**-nostdlib-** を指定したことと同じで、mscorlib.dll がプログラムにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="8622d-107">If you do not specify **-nostdlib**, mscorlib.dll will be imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="8622d-108">**-nostdlib** を指定することは、**-nostdlib+** を指定することと同じです。</span><span class="sxs-lookup"><span data-stu-id="8622d-108">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="8622d-109">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="8622d-109">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="8622d-110">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="8622d-110">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="8622d-111">**[ビルド]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8622d-111">Click the **Build** properties page.</span></span>  
  
3.  <span data-ttu-id="8622d-112">**[詳細設定]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8622d-112">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="8622d-113">**[mscorlib.dll を参照しない]** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="8622d-113">Modify the **Do not reference mscorlib.dll** property.</span></span>  
  
 <span data-ttu-id="8622d-114">このコンパイラ オプションをプログラムで設定する方法については、「 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8622d-114">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8622d-115">参照</span><span class="sxs-lookup"><span data-stu-id="8622d-115">See Also</span></span>  
 [<span data-ttu-id="8622d-116">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="8622d-116">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
