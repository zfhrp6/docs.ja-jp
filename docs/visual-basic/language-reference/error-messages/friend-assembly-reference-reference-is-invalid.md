---
title: "フレンド アセンブリ参照&lt;参照&gt;が正しくありません"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords: BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 39ae94e309ee8d18e6b5317445b7e4b7f6a42af9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a><span data-ttu-id="a713f-102">フレンド アセンブリ参照&lt;参照&gt;が正しくありません</span><span class="sxs-lookup"><span data-stu-id="a713f-102">Friend assembly reference &lt;reference&gt; is invalid</span></span>
<span data-ttu-id="a713f-103">フレンド アセンブリ参照\<参照 > が無効です。</span><span class="sxs-lookup"><span data-stu-id="a713f-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="a713f-104">厳密な名前の署名つきアセンブリはその InternalsVisibleTo 宣言内で公開キーを指定しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="a713f-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="a713f-105">渡すアセンブリ名、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>厳密な名前のアセンブリを識別する属性のコンス トラクターが含まれません、`PublicKey`属性。</span><span class="sxs-lookup"><span data-stu-id="a713f-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="a713f-106">**エラー ID:** BC31535</span><span class="sxs-lookup"><span data-stu-id="a713f-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a713f-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="a713f-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="a713f-108">厳密な名前のフレンド アセンブリの公開キーを確認します。</span><span class="sxs-lookup"><span data-stu-id="a713f-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="a713f-109">渡される、アセンブリ名の一部として、公開キーを含む、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性コンス トラクターを使用して、`PublicKey`属性。</span><span class="sxs-lookup"><span data-stu-id="a713f-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a713f-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="a713f-110">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 [<span data-ttu-id="a713f-111">フレンド アセンブリ</span><span class="sxs-lookup"><span data-stu-id="a713f-111">Friend Assemblies</span></span>](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)  
 [<span data-ttu-id="a713f-112">方法: 署名されたフレンド アセンブリを作成する</span><span class="sxs-lookup"><span data-stu-id="a713f-112">How to: Create Signed Friend Assemblies</span></span>](http://msdn.microsoft.com/library/f5542300-58b4-4e1c-b809-8df11e95e69b)
