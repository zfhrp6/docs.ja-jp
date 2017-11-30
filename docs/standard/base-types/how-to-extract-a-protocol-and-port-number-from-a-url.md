---
title: "方法 : URL からプロトコルとポート番号を抽出する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: ab7f62b3-6d2c-4efb-8ac6-28600df5fd5c
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 10ab05ac8b24c0658be2f27809137c6b0bd4834f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a><span data-ttu-id="588da-102">方法 : URL からプロトコルとポート番号を抽出する</span><span class="sxs-lookup"><span data-stu-id="588da-102">How to: Extract a Protocol and Port Number from a URL</span></span>
<span data-ttu-id="588da-103">次の例では、URL からプロトコルとポート番号を抽出します。</span><span class="sxs-lookup"><span data-stu-id="588da-103">The following example extracts a protocol and port number from a URL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="588da-104">例</span><span class="sxs-lookup"><span data-stu-id="588da-104">Example</span></span>  
 <span data-ttu-id="588da-105">この例では、<xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType>プロトコルを返すメソッドに続けてコロンの後にポート番号。</span><span class="sxs-lookup"><span data-stu-id="588da-105">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method to return the protocol followed by a colon followed by the port number.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 <span data-ttu-id="588da-106">この正規表現パターン `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` の解釈を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="588da-106">The regular expression pattern `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="588da-107">パターン</span><span class="sxs-lookup"><span data-stu-id="588da-107">Pattern</span></span>|<span data-ttu-id="588da-108">説明</span><span class="sxs-lookup"><span data-stu-id="588da-108">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="588da-109">文字列の先頭から照合を開始します。</span><span class="sxs-lookup"><span data-stu-id="588da-109">Begin the match at the start of the string.</span></span>|  
|`(?<proto>\w+)`|<span data-ttu-id="588da-110">1 つ以上の単語文字に一致します。</span><span class="sxs-lookup"><span data-stu-id="588da-110">Match one or more word characters.</span></span> <span data-ttu-id="588da-111">このグループの名前を付けます`proto`です。</span><span class="sxs-lookup"><span data-stu-id="588da-111">Name this group `proto`.</span></span>|  
|`://`|<span data-ttu-id="588da-112">後に 2 つのスラッシュ記号が続くコロンと一致します。</span><span class="sxs-lookup"><span data-stu-id="588da-112">Match a colon followed by two slash marks.</span></span>|  
|`[^/]+?`|<span data-ttu-id="588da-113">スラッシュ記号以外の任意の文字の 1 回以上の (ただし、可能な限り少ない) 出現と一致します。</span><span class="sxs-lookup"><span data-stu-id="588da-113">Match one or more occurrences (but as few as possible) of any character other than a slash mark.</span></span>|  
|`(?<port>:\d+)?`|<span data-ttu-id="588da-114">後に 1 桁以上の文字が続くコロンの 0 回または 1 回の出現と一致します。</span><span class="sxs-lookup"><span data-stu-id="588da-114">Match zero or one occurrence of a colon followed by one or more digit characters.</span></span> <span data-ttu-id="588da-115">このグループの名前を付けます`port`です。</span><span class="sxs-lookup"><span data-stu-id="588da-115">Name this group `port`.</span></span>|  
|`/`|<span data-ttu-id="588da-116">スラッシュ記号に一致します。</span><span class="sxs-lookup"><span data-stu-id="588da-116">Match a slash mark.</span></span>|  
  
 <span data-ttu-id="588da-117"><xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType>メソッドを展開、`${proto}${port}`置換シーケンスは、正規表現パターン内でキャプチャされた 2 つの名前付きグループの値を連結します。</span><span class="sxs-lookup"><span data-stu-id="588da-117">The <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method expands the `${proto}${port}` replacement sequence, which concatenates the value of the two named groups captured in the regular expression pattern.</span></span> <span data-ttu-id="588da-118">代わりに使用する明示的にによって返されるコレクション オブジェクトから取得された文字列を連結するのには、<xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="588da-118">It is a convenient alternative to explicitly concatenating the strings retrieved from the collection object returned by the <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="588da-119">この例では、 <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> 2 つの代替文字列を持つメソッド`${proto}`と`${port}`、出力文字列に、キャプチャされたグループを含める。</span><span class="sxs-lookup"><span data-stu-id="588da-119">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method with two substitutions, `${proto}` and `${port}`, to include the captured groups in the output string.</span></span> <span data-ttu-id="588da-120">キャプチャされたグループを取得するにはパターン一致から<xref:System.Text.RegularExpressions.GroupCollection>オブジェクトの代わりに、コードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="588da-120">You can retrieve the captured groups from the match's <xref:System.Text.RegularExpressions.GroupCollection> object instead, as the following code shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="588da-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="588da-121">See Also</span></span>  
 [<span data-ttu-id="588da-122">.NET の正規表現</span><span class="sxs-lookup"><span data-stu-id="588da-122">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
