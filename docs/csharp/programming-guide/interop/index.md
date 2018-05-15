---
title: 相互運用性 (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: e854c51bd80809b92bb538475a407422b2eba7c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="cb39c-102">相互運用性 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="cb39c-102">Interoperability (C# Programming Guide)</span></span>
<span data-ttu-id="cb39c-103">相互運用性は、アンマネージ コードへの既存の投資を保持して活用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="cb39c-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="cb39c-104">共通言語ランタイム (CLR) の制御下で実行されるコードは*マネージ コード*と呼ばれ、CLR の外部で実行されるコードは*アンマネージ コード*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="cb39c-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="cb39c-105">アンマネージ コードの例は、COM、COM +、C++ コンポーネント、ActiveX コンポーネント、および Microsoft Win32 API です。</span><span class="sxs-lookup"><span data-stu-id="cb39c-105">COM, COM+, C++ components, ActiveX components, and Microsoft Win32 API are examples of unmanaged code.</span></span>  
  
 <span data-ttu-id="cb39c-106">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] では、プラットフォーム呼び出しサービス、<xref:System.Runtime.InteropServices> 名前空間、C++ 相互運用性、および COM 相互運用性 (COM 相互運用機能) を通して、アンマネージ コードの相互運用を可能にしています。</span><span class="sxs-lookup"><span data-stu-id="cb39c-106">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cb39c-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="cb39c-107">In This Section</span></span>  
 [<span data-ttu-id="cb39c-108">相互運用性の概要</span><span class="sxs-lookup"><span data-stu-id="cb39c-108">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 <span data-ttu-id="cb39c-109">C# のマネージ コードとアンマネージ コードの間で相互運用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb39c-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="cb39c-110">方法: Visual C# の機能を使用して Office 相互運用オブジェクトにアクセスする</span><span class="sxs-lookup"><span data-stu-id="cb39c-110">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="cb39c-111">Office のプログラミングを容易にするために Visual C# に導入されている機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb39c-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="cb39c-112">方法: COM 相互運用機能を使用したプログラミングでインデックス付きプロパティを使用する</span><span class="sxs-lookup"><span data-stu-id="cb39c-112">How to: Use Indexed Properties in COM Interop Programming</span></span>](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="cb39c-113">インデックス付きプロパティを使用して、パラメーターを持つ COM プロパティにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb39c-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="cb39c-114">方法: プラットフォーム呼び出しを使用して Wave ファイルを再生する</span><span class="sxs-lookup"><span data-stu-id="cb39c-114">How to: Use Platform Invoke to Play a Wave File</span></span>](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="cb39c-115">プラットフォーム呼び出しサービスを使用して、Windows オペレーティング システム上の .wav サウンド ファイルを再生する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb39c-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="cb39c-116">チュートリアル: Office のプログラミング</span><span class="sxs-lookup"><span data-stu-id="cb39c-116">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 <span data-ttu-id="cb39c-117">Excel ブックと、ブックへのリンクを含む Word 文書を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cb39c-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="cb39c-118">COM クラスの例</span><span class="sxs-lookup"><span data-stu-id="cb39c-118">Example COM Class</span></span>](../../../csharp/programming-guide/interop/example-com-class.md)  
 <span data-ttu-id="cb39c-119">C# クラスを COM オブジェクトとして公開する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cb39c-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="cb39c-120">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="cb39c-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cb39c-121">参照</span><span class="sxs-lookup"><span data-stu-id="cb39c-121">See Also</span></span>  
 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="cb39c-122">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="cb39c-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cb39c-123">アンマネージ コードとの相互運用</span><span class="sxs-lookup"><span data-stu-id="cb39c-123">Interoperating with Unmanaged Code</span></span>](../../../../docs/framework/interop/index.md)  
 [<span data-ttu-id="cb39c-124">チュートリアル: Office のプログラミング</span><span class="sxs-lookup"><span data-stu-id="cb39c-124">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
