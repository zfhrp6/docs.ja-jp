---
title: "方法 : 厳密な名前のアセンブリを参照する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b005926f99b7c151e5916a95a9852dd8b448a928
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-reference-a-strong-named-assembly"></a><span data-ttu-id="65871-102">方法 : 厳密な名前のアセンブリを参照する</span><span class="sxs-lookup"><span data-stu-id="65871-102">How to: Reference a Strong-Named Assembly</span></span>
<span data-ttu-id="65871-103">通常、厳密な名前付きアセンブリ内にある型またはリソースを参照するプロセスは透過的です。</span><span class="sxs-lookup"><span data-stu-id="65871-103">The process for referencing types or resources in a strong-named assembly is usually transparent.</span></span> <span data-ttu-id="65871-104">コンパイル時 (事前バインディング) または実行時に参照を作成できます。</span><span class="sxs-lookup"><span data-stu-id="65871-104">You can make the reference either at compile time (early binding) or at run time.</span></span>  
  
 <span data-ttu-id="65871-105">コンパイル時参照は、あるアセンブリが別のアセンブリを明示的に参照することをコンパイラに対して指定するときに発生します。</span><span class="sxs-lookup"><span data-stu-id="65871-105">A compile-time reference occurs when you indicate to the compiler that your assembly explicitly references another assembly.</span></span> <span data-ttu-id="65871-106">コンパイル時参照を使用する場合、コンパイラは対象の厳密な名前付きアセンブリの公開キーを自動的に取得し、その公開キーをコンパイルされるアセンブリのアセンブリ参照内に自動的に配置します。</span><span class="sxs-lookup"><span data-stu-id="65871-106">When you use compile-time referencing, the compiler automatically gets the public key of the targeted strong-named assembly and places it in the assembly reference of the assembly being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65871-107">厳密な名前のアセンブリは、他の厳密な名前のアセンブリでのタイプだけを使用できます。</span><span class="sxs-lookup"><span data-stu-id="65871-107">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="65871-108">それ以外の場合は、厳密な名前のアセンブリのセキュリティが損なわれます。</span><span class="sxs-lookup"><span data-stu-id="65871-108">Otherwise, the security of the strong-named assembly would be compromised.</span></span>  
  
### <a name="to-make-a-compile-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="65871-109">厳密な名前付きアセンブリへのコンパイル時参照を作成するには</span><span class="sxs-lookup"><span data-stu-id="65871-109">To make a compile-time reference to a strong-named assembly</span></span>  
  
1.  <span data-ttu-id="65871-110">コマンド プロンプトに次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="65871-110">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="65871-111">\<*compiler command*> **/reference:**\<*assembly name*></span><span class="sxs-lookup"><span data-stu-id="65871-111">\<*compiler command*> **/reference:**\<*assembly name*></span></span>  
  
     <span data-ttu-id="65871-112">このコマンドで、*compiler command* は、使用している言語のコンパイラ コマンドです。*assembly name* は、参照される厳密な名前付きアセンブリの名前です。</span><span class="sxs-lookup"><span data-stu-id="65871-112">In this command, *compiler command* is the compiler command for the language you are using, and *assembly name* is the name of the strong-named assembly being referenced.</span></span> <span data-ttu-id="65871-113">ライブラリ アセンブリを作成するための **/t:library** オプションなどの他のコンパイラ オプションも使用できます。</span><span class="sxs-lookup"><span data-stu-id="65871-113">You can also use other compiler options, such as the **/t:library** option for creating a library assembly.</span></span>  
  
 <span data-ttu-id="65871-114">`myAssembly.cs` というコード モジュールから厳密な名前付きアセンブリ `myLibAssembly.dll` を参照するアセンブリ `myAssembly.dll` を作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="65871-114">The following example creates an assembly called `myAssembly.dll` that references a strong-named assembly called `myLibAssembly.dll` from a code module called `myAssembly.cs`.</span></span>  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### <a name="to-make-a-run-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="65871-115">厳密な名前付きアセンブリへの実行時参照を作成するには</span><span class="sxs-lookup"><span data-stu-id="65871-115">To make a run-time reference to a strong-named assembly</span></span>  
  
1.  <span data-ttu-id="65871-116"><xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> メソッドまたは <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> メソッドを使用するなどの方法で、実行時に厳密な名前付きアセンブリ参照を作成する場合は、参照される厳密な名前付きアセンブリの表示名を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65871-116">When you make a run-time reference to a strong-named assembly (for example, by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> method), you must use the display name of the referenced strong-named assembly.</span></span> <span data-ttu-id="65871-117">表示名の構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="65871-117">The syntax of a display name is as follows:</span></span>  
  
     <span data-ttu-id="65871-118">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span><span class="sxs-lookup"><span data-stu-id="65871-118">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span></span>  
  
     <span data-ttu-id="65871-119">例:</span><span class="sxs-lookup"><span data-stu-id="65871-119">For example:</span></span>  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     <span data-ttu-id="65871-120">この例では、`PublicKeyToken` は 16 進形式の公開キートークンです。</span><span class="sxs-lookup"><span data-stu-id="65871-120">In this example, `PublicKeyToken` is the hexadecimal form of the public key token.</span></span> <span data-ttu-id="65871-121">カルチャの値がない場合は、`Culture=neutral` を使用します。</span><span class="sxs-lookup"><span data-stu-id="65871-121">If there is no culture value, use `Culture=neutral`.</span></span>  
  
 <span data-ttu-id="65871-122">この情報を <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> メソッドで使用する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="65871-122">The following code example shows how to use this information with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)]
 [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)]
 [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 <span data-ttu-id="65871-123">特定のアセンブリの 16 進形式の公開キーと公開キー トークンは、次の[厳密名 (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) コマンドを使用して出力できます。</span><span class="sxs-lookup"><span data-stu-id="65871-123">You can print the hexadecimal format of the public key and public key token for a specific assembly by using the following [Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) command:</span></span>  
  
 <span data-ttu-id="65871-124">**sn -Tp \<** *assembly* **>**</span><span class="sxs-lookup"><span data-stu-id="65871-124">**sn -Tp \<** *assembly* **>**</span></span>  
  
 <span data-ttu-id="65871-125">公開キーファイルがある場合は、代わりに次のコマンドを使用できます (コマンド ライン オプションの大文字と小文字の違いに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="65871-125">If you have a public key file, you can use the following command instead (note the difference in case on the command-line option):</span></span>  
  
 <span data-ttu-id="65871-126">**sn -tp \<** *assembly* **>**</span><span class="sxs-lookup"><span data-stu-id="65871-126">**sn -tp \<** *assembly* **>**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65871-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="65871-127">See Also</span></span>  
 [<span data-ttu-id="65871-128">厳密な名前付きアセンブリの作成と使用</span><span class="sxs-lookup"><span data-stu-id="65871-128">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
