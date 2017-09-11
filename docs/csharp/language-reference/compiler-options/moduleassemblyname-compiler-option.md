---
title: "-moduleassemblyname (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /moduleassemblyname
dev_langs:
- CSharp
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
caps.latest.revision: 10
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
ms.openlocfilehash: 2522609aa41ad944b37a8882c1cc56cd5967b330
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="moduleassemblyname-c-compiler-option"></a><span data-ttu-id="24e11-102">/moduleassemblyname (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="24e11-102">/moduleassemblyname (C# Compiler Option)</span></span>
<span data-ttu-id="24e11-103">.netmodule がアクセスできる非パブリック型のアセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="24e11-103">Specifies an assembly whose non-public types a .netmodule can access.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24e11-104">構文</span><span class="sxs-lookup"><span data-stu-id="24e11-104">Syntax</span></span>  
  
```console  
/moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="24e11-105">引数</span><span class="sxs-lookup"><span data-stu-id="24e11-105">Arguments</span></span>  
 `assembly_name`  
 <span data-ttu-id="24e11-106">.netmodule がアクセスできる非パブリック型のアセンブリの名前です。</span><span class="sxs-lookup"><span data-stu-id="24e11-106">The name of the assembly whose non-public types the .netmodule can access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24e11-107">コメント</span><span class="sxs-lookup"><span data-stu-id="24e11-107">Remarks</span></span>  
 <span data-ttu-id="24e11-108">**/moduleassemblyname** は、.netmodule をビルドする場合と、次の条件に当てはまる場合に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24e11-108">**/moduleassemblyname** should be used when building a .netmodule, and where the following conditions are true:</span></span>  
  
-   <span data-ttu-id="24e11-109">.netmodule で、既存のアセンブリ内の非パブリック型へのアクセスが必要な場合。</span><span class="sxs-lookup"><span data-stu-id="24e11-109">The .netmodule needs access to non-public types in an existing assembly.</span></span>  
  
-   <span data-ttu-id="24e11-110">.netmodule をビルドするアセンブリの名前を把握していること。</span><span class="sxs-lookup"><span data-stu-id="24e11-110">You know the name of the assembly into which the .netmodule will be built.</span></span>  
  
-   <span data-ttu-id="24e11-111">既存のアセンブリに、.netmodule をビルドするアセンブリへのフレンド アセンブリのアクセス権が付与されていること。</span><span class="sxs-lookup"><span data-stu-id="24e11-111">The existing assembly has granted friend assembly access to the assembly into which the .netmodule will be built.</span></span>  
  
 <span data-ttu-id="24e11-112">.netmodule のビルドの詳細については、「[/target:module (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24e11-112">For more information on building a .netmodule, see [/target:module (C# Compiler Options)](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="24e11-113">フレンド アセンブリの詳細については、「[フレンド アセンブリ](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24e11-113">For more information on friend assemblies, see [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span></span>  
  
 <span data-ttu-id="24e11-114">このオプションは、開発環境からは利用できません。これはコマンドラインからコンパイルするときにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="24e11-114">This option is not available from within the development environment; it is only available when compiling from the command line.</span></span>  
  
 <span data-ttu-id="24e11-115">このコンパイラ オプションは Visual Studio では使用できず、プログラムで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="24e11-115">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24e11-116">例</span><span class="sxs-lookup"><span data-stu-id="24e11-116">Example</span></span>  
 <span data-ttu-id="24e11-117">このサンプルは、csman_an_assembly というアセンブリへのフレンド アセンブリのアクセス権を付与する、プライベート型のアセンブリをビルドします。</span><span class="sxs-lookup"><span data-stu-id="24e11-117">This sample builds an assembly with a private type, and that gives friend assembly access to an assembly called csman_an_assembly.</span></span>  
  
```csharp  
// moduleassemblyname_1.cs  
// compile with: /target:library  
using System;  
using System.Runtime.CompilerServices;  
  
[assembly:InternalsVisibleTo ("csman_an_assembly")]  
  
class An_Internal_Class   
{  
    public void Test()   
    {   
        Console.WriteLine("An_Internal_Class.Test called");   
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="24e11-118">例</span><span class="sxs-lookup"><span data-stu-id="24e11-118">Example</span></span>  
 <span data-ttu-id="24e11-119">このサンプルは、アセンブリ moduleassemblyname_1.dll 内の非パブリック型にアクセスする .netmodule をビルドします。</span><span class="sxs-lookup"><span data-stu-id="24e11-119">This sample builds a .netmodule that accesses a non-public type in the assembly moduleassemblyname_1.dll.</span></span> <span data-ttu-id="24e11-120">この .netmodule が csman_an_assembly というアセンブリにビルドされることがわかっていれば、**/moduleassemblyname** を指定して、csman_an_assembly へのフレンド アセンブリのアクセス権が付与されているアセンブリ内の非パブリック型へのアクセスを .netmodule に許可することができます。</span><span class="sxs-lookup"><span data-stu-id="24e11-120">By knowing that this .netmodule will be built into an assembly called csman_an_assembly, we can specify **/moduleassemblyname**, allowing the .netmodule to access non-public types in an assembly that has granted friend assembly access to csman_an_assembly.</span></span>  
  
```csharp  
// moduleassemblyname_2.cs  
// compile with: /moduleassemblyname:csman_an_assembly /target:module /reference:moduleassemblyname_1.dll  
class B {  
    public void Test() {  
        An_Internal_Class x = new An_Internal_Class();  
        x.Test();  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="24e11-121">例</span><span class="sxs-lookup"><span data-stu-id="24e11-121">Example</span></span>  
 <span data-ttu-id="24e11-122">このコード サンプルは、既にビルドされたアセンブリと .netmodule を参照する、アセンブリ csman_an_assembly をビルドします。</span><span class="sxs-lookup"><span data-stu-id="24e11-122">This code sample builds the assembly csman_an_assembly, referencing the previously-built assembly and .netmodule.</span></span>  
  
```csharp  
// csman_an_assembly.cs  
// compile with: /addmodule:moduleassemblyname_2.netmodule /reference:moduleassemblyname_1.dll  
class A {  
    public static void Main() {  
        B bb = new B();  
        bb.Test();  
    }  
}  
```  
  
 <span data-ttu-id="24e11-123">**An_Internal_Class.Test called**</span><span class="sxs-lookup"><span data-stu-id="24e11-123">**An_Internal_Class.Test called**</span></span>   
## <a name="see-also"></a><span data-ttu-id="24e11-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="24e11-124">See Also</span></span>  
 <span data-ttu-id="24e11-125">[C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="24e11-125">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="24e11-126">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="24e11-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

