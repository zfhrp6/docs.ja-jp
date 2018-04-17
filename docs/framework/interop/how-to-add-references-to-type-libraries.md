---
title: '方法: タイプ ライブラリへの参照を追加する'
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 561e05c82c1882ad5e495ddb3dc1a17356522514
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-references-to-type-libraries"></a><span data-ttu-id="02ba2-102">方法: タイプ ライブラリへの参照を追加する</span><span class="sxs-lookup"><span data-stu-id="02ba2-102">How to: Add References to Type Libraries</span></span>
<span data-ttu-id="02ba2-103">Visual Studio は、タイプ ライブラリに参照を追加する際に、メタデータを含む相互運用機能アセンブリを生成します。</span><span class="sxs-lookup"><span data-stu-id="02ba2-103">Visual Studio generates an interop assembly containing metadata when you add a reference to a type library.</span></span> <span data-ttu-id="02ba2-104">プライマリ相互運用機能アセンブリが使用可能な場合、Visual Studio では、新しい相互運用機能アセンブリを生成する前に既存のアセンブリが使用されます。</span><span class="sxs-lookup"><span data-stu-id="02ba2-104">If a primary interop assembly is available, Visual Studio uses the existing assembly before generating a new interop assembly.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a><span data-ttu-id="02ba2-105">Visual Studio でタイプ ライブラリへの参照を追加するには</span><span class="sxs-lookup"><span data-stu-id="02ba2-105">To add a reference to a type library in Visual Studio</span></span>  
  
1.  <span data-ttu-id="02ba2-106">Windows Setup.exe ファイルで COM DLL ファイルまたは EXE ファイルがインストールされない場合は、このファイルをコンピューターにインストールします。</span><span class="sxs-lookup"><span data-stu-id="02ba2-106">Install the COM DLL or EXE file on your computer, unless a Windows Setup.exe file performs the installation for you.</span></span>  
  
2.  <span data-ttu-id="02ba2-107">**[プロジェクト]**、**[参照の追加]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="02ba2-107">Choose **Project**, **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="02ba2-108">参照マネージャーで、**[COM]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="02ba2-108">In the Reference Manager, choose **COM**.</span></span>  
  
4.  <span data-ttu-id="02ba2-109">一覧からタイプ ライブラリを選択するか、.tlb ファイルを参照します。</span><span class="sxs-lookup"><span data-stu-id="02ba2-109">Select the type library from the list, or browse for the .tlb file.</span></span>  
  
5.  <span data-ttu-id="02ba2-110">**[OK]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="02ba2-110">Choose **OK**.</span></span>  
  
6.  <span data-ttu-id="02ba2-111">ソリューション エクスプローラーで、追加した参照のショートカット メニューを開き、**[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="02ba2-111">In Solution Explorer, open the shortcut menu for the reference you just added, and then choose **Properties**.</span></span>  
  
7.  <span data-ttu-id="02ba2-112">**[プロパティ]** ウィンドウで、**[相互運用機能型の埋め込み]** プロパティが **[True]** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="02ba2-112">In the **Properties** window, make sure that the **Embed Interop Types** property is set to **True**.</span></span> <span data-ttu-id="02ba2-113">その結果、Visual Studio により、COM 型の型情報が実行可能ファイルに埋め込まれ、アプリでプライマリ相互運用機能アセンブリを配置する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="02ba2-113">This causes Visual Studio to embed type information for COM types in your executables, eliminating the need to deploy primary interop assemblies with your app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02ba2-114">メニュー オプションおよびダイアログ ボックス オプションは、使用中の Visula Studio のバージョンによって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="02ba2-114">The menu and dialog box options may vary depending on the version of Visual Studio you're using.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a><span data-ttu-id="02ba2-115">コマンド ライン コンパイルのために参照をタイプ ライブラリに追加するには</span><span class="sxs-lookup"><span data-stu-id="02ba2-115">To add a reference to a type library for command-line compilation</span></span>  
  
1.  <span data-ttu-id="02ba2-116">「[How to: Generate Interop Assemblies from Type Libraries](how-to-generate-interop-assemblies-from-type-libraries.md)」(方法: 相互運用機能アセンブリをタイプ ライブラリから生成する) の説明に従って、相互運用機能アセンブリを生成します。</span><span class="sxs-lookup"><span data-stu-id="02ba2-116">Generate an interop assembly as described in [How to: Generate Interop Assemblies from Type Libraries](how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>  
  
2.  <span data-ttu-id="02ba2-117">相互運用機能アセンブリ名を指定して [/link (C# コンパイラ オプション)](../../csharp/language-reference/compiler-options/link-compiler-option.md) または [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) コンパイラ オプションを使用し、COM 型の型情報を実行可能ファイルに埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="02ba2-117">Use the [/link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler option with the interop assembly name to embed type information for COM types in your executables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02ba2-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="02ba2-118">See Also</span></span>  
 [<span data-ttu-id="02ba2-119">タイプ ライブラリのアセンブリとしてのインポート</span><span class="sxs-lookup"><span data-stu-id="02ba2-119">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)  
 [<span data-ttu-id="02ba2-120">.NET Framework への COM コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="02ba2-120">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)  
 <span data-ttu-id="02ba2-121">[チュートリアル: Microsoft Office アセンブリからの型情報の埋め込み](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="02ba2-121">[Walkthrough: Embedding Type Information from Microsoft Office Assemblies](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))</span></span>  
 [<span data-ttu-id="02ba2-122">チュートリアル: マネージ アセンブリからの型の埋め込み</span><span class="sxs-lookup"><span data-stu-id="02ba2-122">Walkthrough: Embedding Types from Managed Assemblies</span></span>](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [<span data-ttu-id="02ba2-123">/link (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="02ba2-123">/link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)  
 [<span data-ttu-id="02ba2-124">/link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02ba2-124">/link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
