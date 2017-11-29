---
title: "方法: 公開キーと秘密キーのキー ペアを作成する"
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
- key pairs for strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- cryptographic key pairs
- snk files (key pair files)
- public-private key pairs
- .snk files
- strong-named assemblies, key pairs
ms.assetid: 05026813-f3bd-4d7c-9e0b-fc588eb3d114
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a0d1f54b417a9752ae96e52f78d9df7d2d60cbec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-public-private-key-pair"></a><span data-ttu-id="6c67a-102">方法: 公開キーと秘密キーのキー ペアを作成する</span><span class="sxs-lookup"><span data-stu-id="6c67a-102">How to: Create a Public-Private Key Pair</span></span>
<span data-ttu-id="6c67a-103">アセンブリに厳密な名前で署名するには、公開/秘密キーの組み合わせが必要です。</span><span class="sxs-lookup"><span data-stu-id="6c67a-103">To sign an assembly with a strong name, you must have a public/private key pair.</span></span> <span data-ttu-id="6c67a-104">このような公開キーと秘密キーからなる暗号鍵の組み合わせがコンパイル時に利用され、厳密な名前が付いたアセンブリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6c67a-104">This public and private cryptographic key pair is used during compilation to create a strong-named assembly.</span></span> <span data-ttu-id="6c67a-105">キーの組み合わせは[厳密名ツール (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) を利用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="6c67a-105">You can create a key pair using the [Strong Name tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).</span></span> <span data-ttu-id="6c67a-106">キー ペア ファイルには通常、.snk 拡張子が与えられます。</span><span class="sxs-lookup"><span data-stu-id="6c67a-106">Key pair files usually have an .snk extension.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c67a-107">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] では、C# と Visual Basic のプロジェクト プロパティ ページに **[署名]** タブがあります。このタブで、既存のキー ファイルを選択したり、新しいキー ファイルを生成したりできます。Sn.exe を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6c67a-107">In [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], the C# and Visual Basic project property pages include a **Signing** tab that enables you to select existing key files or to generate new key files without using Sn.exe.</span></span> <span data-ttu-id="6c67a-108">Visual C++ では、**[プロパティ ページ]** ウィンドウの **[構成プロパティ]** セクションの **[リンカー]** セクションの **[詳細設定]** プロパティ ページで既存のキー ファイルの場所を指定できます。</span><span class="sxs-lookup"><span data-stu-id="6c67a-108">In Visual C++, you can specify the location of an existing key file in the **Advanced** property page in the **Linker** section of the **Configuration Properties** section of the **Property Pages** window.</span></span> <span data-ttu-id="6c67a-109">[!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] より、キー ファイル ペアを特定する <xref:System.Reflection.AssemblyKeyFileAttribute> 属性を使用できなくなりました。</span><span class="sxs-lookup"><span data-stu-id="6c67a-109">The use of the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute to identify key file pairs has been made obsolete beginning with [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)].</span></span>  
  
### <a name="to-create-a-key-pair"></a><span data-ttu-id="6c67a-110">キー ペアを作成するには</span><span class="sxs-lookup"><span data-stu-id="6c67a-110">To create a key pair</span></span>  
  
1.  <span data-ttu-id="6c67a-111">コマンド プロンプトに次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="6c67a-111">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="6c67a-112">**sn –k** \<*ファイル名*></span><span class="sxs-lookup"><span data-stu-id="6c67a-112">**sn –k** \<*file name*></span></span>  
  
     <span data-ttu-id="6c67a-113">このコマンドでは、*ファイル名*はキー ペアを含む出力ファイルの名前になります。</span><span class="sxs-lookup"><span data-stu-id="6c67a-113">In this command, *file name* is the name of the output file containing the key pair.</span></span>  
  
 <span data-ttu-id="6c67a-114">次の例では、`sgKey.snk` という名前のキー ペアが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6c67a-114">The following example creates a key pair called `sgKey.snk`.</span></span>  
  
```  
sn -k sgKey.snk  
```  
  
 <span data-ttu-id="6c67a-115">アセンブリに遅延署名する予定であり、キー ペア全体を制御する (テスト シナリオの範囲を超えることは予期されない) のであれば、次のコマンドを利用してキー ペアを生成し、それから個別ファイルに公開キーを抽出できます。</span><span class="sxs-lookup"><span data-stu-id="6c67a-115">If you intend to delay sign an assembly and you control the whole key pair (which is unlikely outside test scenarios), you can use the following commands to generate a key pair and then extract the public key from it into a separate file.</span></span> <span data-ttu-id="6c67a-116">最初に、キー ペアを作成します。</span><span class="sxs-lookup"><span data-stu-id="6c67a-116">First, create the key pair:</span></span>  
  
```  
sn -k keypair.snk  
```  
  
 <span data-ttu-id="6c67a-117">次に、キー ペアから公開キーを抽出し、それを個別ファイルにコピーします。</span><span class="sxs-lookup"><span data-stu-id="6c67a-117">Next, extract the public key from the key pair and copy it to a separate file:</span></span>  
  
```  
sn -p keypair.snk public.snk  
```  
  
 <span data-ttu-id="6c67a-118">キー ペアを作成したら、厳密な名前の署名ツールで見つけられる場所にファイルを置く必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c67a-118">Once you create the key pair, you must put the file where the strong name signing tools can find it.</span></span>  
  
 <span data-ttu-id="6c67a-119">厳密な名前でアセンブリに署名すると、[アセンブリ リンカー (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) は、現在のディレクトリと出力ディレクトリを基準にしてキー ファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="6c67a-119">When signing an assembly with a strong name, the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) looks for the key file relative to the current directory and to the output directory.</span></span> <span data-ttu-id="6c67a-120">コマンド ライン コンパイラを使用する場合は、コード モジュールを格納する現在のディレクトリにキーをコピーするだけで十分です。</span><span class="sxs-lookup"><span data-stu-id="6c67a-120">When using command-line compilers, you can simply copy the key to the current directory containing your code modules.</span></span>  
  
 <span data-ttu-id="6c67a-121">プロジェクト プロパティに **[署名]** タブがない以前のバージョンの [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] を利用している場合、キー ファイルの推奨場所はファイル属性が次のように指定されたプロジェクト ディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="6c67a-121">If you are using an earlier version of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] that does not have a **Signing** tab in the project properties, the recommended key file location is the project directory with the file attribute specified as follows:</span></span>  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="6c67a-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="6c67a-122">See Also</span></span>  
 [<span data-ttu-id="6c67a-123">厳密な名前付きアセンブリの作成と使用</span><span class="sxs-lookup"><span data-stu-id="6c67a-123">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
