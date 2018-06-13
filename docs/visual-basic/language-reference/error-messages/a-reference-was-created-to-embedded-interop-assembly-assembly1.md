---
title: 埋め込まれた相互運用機能アセンブリの参照が作成された&#39; &lt;assembly1&gt; &#39;アセンブリからそのアセンブリへの間接参照のため&#39; &lt;assembly2&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
ms.openlocfilehash: 43a441b6b99988ae1b47969dde9c4bc815820767
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588133"
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-39ltassembly1gt39-because-of-an-indirect-reference-to-that-assembly-from-assembly-39ltassembly2gt39"></a><span data-ttu-id="b7e1f-102">埋め込まれた相互運用機能アセンブリの参照が作成された&#39; &lt;assembly1&gt; &#39;アセンブリからそのアセンブリへの間接参照のため&#39; &lt;assembly2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="b7e1f-102">A reference was created to embedded interop assembly &#39;&lt;assembly1&gt;&#39; because of an indirect reference to that assembly from assembly &#39;&lt;assembly2&gt;&#39;</span></span>
<span data-ttu-id="b7e1f-103">埋め込まれた相互運用機能アセンブリ '\<assembly1>' への参照が作成されました。これは、そのアセンブリへの間接参照がアセンブリ '\<assembly2>' によって作成されたためです。</span><span class="sxs-lookup"><span data-stu-id="b7e1f-103">A reference was created to embedded interop assembly '\<assembly1>' because of an indirect reference to that assembly from assembly '\<assembly2>'.</span></span> <span data-ttu-id="b7e1f-104">両方のアセンブリで '相互運用機能型の埋め込み' プロパティを変更することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="b7e1f-104">Consider changing the 'Embed Interop Types' property on either assembly.</span></span>  
  
 <span data-ttu-id="b7e1f-105">`Embed Interop Types` プロパティが `True` に設定されたアセンブリ (assembly1) に参照を追加しました。</span><span class="sxs-lookup"><span data-stu-id="b7e1f-105">You have added a reference to an assembly (assembly1) that has the `Embed Interop Types` property set to `True`.</span></span> <span data-ttu-id="b7e1f-106">これにより、コンパイラは、このアセンブリから相互運用機能の型情報を埋め込むよう指示されます。</span><span class="sxs-lookup"><span data-stu-id="b7e1f-106">This instructs the compiler to embed interop type information from that assembly.</span></span> <span data-ttu-id="b7e1f-107">ただし、参照していた別のアセンブリ (assembly2) もこのアセンブリ (assembly1) を参照しており、また `Embed Interop Types` プロパティが `False` に設定されているため、コンパイラはこのアセンブリから相互運用機能の型情報を埋め込むことができません。</span><span class="sxs-lookup"><span data-stu-id="b7e1f-107">However, the compiler cannot embed interop type information from that assembly because another assembly that you have referenced (assembly2) also references that assembly (assembly1) and has the `Embed Interop Types` property set to `False`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7e1f-108">アセンブリ参照の `Embed Interop Types` プロパティを `True` に設定することは、コマンド ライン コンパイラの `/link` オプションを使用してアセンブリを参照することと同じです。</span><span class="sxs-lookup"><span data-stu-id="b7e1f-108">Setting the `Embed Interop Types` property on an assembly reference to `True` is equivalent to referencing the assembly by using the `/link` option for the command-line compiler.</span></span>  
  
 <span data-ttu-id="b7e1f-109">**エラー ID:** BC40059</span><span class="sxs-lookup"><span data-stu-id="b7e1f-109">**Error ID:** BC40059</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="b7e1f-110">この警告に対処するには</span><span class="sxs-lookup"><span data-stu-id="b7e1f-110">To address this warning</span></span>  
  
-   <span data-ttu-id="b7e1f-111">両方のアセンブリに相互運用の型情報を埋め込むには、assembly1 へのすべての参照の `Embed Interop Types` プロパティを `True` に設定します。</span><span class="sxs-lookup"><span data-stu-id="b7e1f-111">To embed interop type information for both assemblies, set the `Embed Interop Types` property on all references to assembly1 to `True`.</span></span>  
  
-   <span data-ttu-id="b7e1f-112">assembly1 の `Embed Interop Types` プロパティを `False` に設定すると警告を回避できます。</span><span class="sxs-lookup"><span data-stu-id="b7e1f-112">To remove the warning, you can set the `Embed Interop Types` property of assembly1 to `False`.</span></span> <span data-ttu-id="b7e1f-113">この例では、相互運用機能型の詳細については、プライマリ相互運用機能アセンブリ (PIA) によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="b7e1f-113">In this case, interop type information is provided by a primary interop assembly (PIA).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7e1f-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7e1f-114">See Also</span></span>  
 [<span data-ttu-id="b7e1f-115">/link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7e1f-115">/link (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/link.md)  
 [<span data-ttu-id="b7e1f-116">アンマネージ コードとの相互運用</span><span class="sxs-lookup"><span data-stu-id="b7e1f-116">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
