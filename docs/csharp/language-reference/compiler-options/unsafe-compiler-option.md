---
title: "-unsafe (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /unsafe
dev_langs:
- CSharp
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.assetid: fdb77ed9-da03-45bd-bb7f-250704da1bcc
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8f285af57d6a06d38d20b2c28e4a637fbc3ecf2c
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="unsafe-c-compiler-options"></a><span data-ttu-id="2ad06-102">/unsafe (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="2ad06-102">/unsafe (C# Compiler Options)</span></span>
<span data-ttu-id="2ad06-103">**/unsafe** コンパイラ オプションは、[unsafe](../../../csharp/language-reference/keywords/unsafe.md) キーワードを使用するコードをコンパイルできるようにします。</span><span class="sxs-lookup"><span data-stu-id="2ad06-103">The **/unsafe** compiler option allows code that uses the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ad06-104">構文</span><span class="sxs-lookup"><span data-stu-id="2ad06-104">Syntax</span></span>  
  
```console  
/unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="2ad06-105">コメント</span><span class="sxs-lookup"><span data-stu-id="2ad06-105">Remarks</span></span>  
 <span data-ttu-id="2ad06-106">アンセーフ コードの詳細については、「[アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ad06-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="2ad06-107">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="2ad06-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="2ad06-108">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="2ad06-108">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="2ad06-109">**[ビルド]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2ad06-109">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="2ad06-110">**[アンセーフ コードの許可]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="2ad06-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
 <span data-ttu-id="2ad06-111">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ad06-111">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ad06-112">例</span><span class="sxs-lookup"><span data-stu-id="2ad06-112">Example</span></span>  
 <span data-ttu-id="2ad06-113">unsafe モードで `in.cs` をコンパイルする場合は、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="2ad06-113">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc /unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="2ad06-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ad06-114">See Also</span></span>  
 <span data-ttu-id="2ad06-115">[C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="2ad06-115">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="2ad06-116">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="2ad06-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

