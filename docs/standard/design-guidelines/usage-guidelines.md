---
title: "使用方法のガイドライン"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3f0a38c69dc286587e702b80ef4093bb98d78b5a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="usage-guidelines"></a><span data-ttu-id="725f8-102">使用方法のガイドライン</span><span class="sxs-lookup"><span data-stu-id="725f8-102">Usage Guidelines</span></span>
<span data-ttu-id="725f8-103">このセクションには、パブリックにアクセスできる Api の一般的な種類の使用に関するガイドラインが含まれています。</span><span class="sxs-lookup"><span data-stu-id="725f8-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="725f8-104">組み込みフレームワーク型 (シリアル化属性など) および一般的な演算子をオーバー ロードの直接の使用状況を処理します。</span><span class="sxs-lookup"><span data-stu-id="725f8-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>  
  
 <span data-ttu-id="725f8-105"><xref:System.IDisposable?displayProperty=nameWithType>インターフェイスは、このセクションでは説明しませんが、については、 [Dispose パターン](../../../docs/standard/design-guidelines/dispose-pattern.md)セクションです。</span><span class="sxs-lookup"><span data-stu-id="725f8-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../../../docs/standard/design-guidelines/dispose-pattern.md) section.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="725f8-106">ガイドラインとその他の一般的なに関する追加情報、組み込みの .NET Framework 型を参照してください、次の参照トピック: <xref:System.DateTime?displayProperty=nameWithType>、 <xref:System.DateTimeOffset?displayProperty=nameWithType>、 <xref:System.ICloneable?displayProperty=nameWithType>、 <xref:System.IComparable%601?displayProperty=nameWithType>、 <xref:System.IEquatable%601?displayProperty=nameWithType>、 <xref:System.Nullable%601?displayProperty=nameWithType>、 <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="725f8-106">For guidelines and additional information about about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="725f8-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="725f8-107">In This Section</span></span>  
 [<span data-ttu-id="725f8-108">配列</span><span class="sxs-lookup"><span data-stu-id="725f8-108">Arrays</span></span>](../../../docs/standard/design-guidelines/arrays.md)  
 [<span data-ttu-id="725f8-109">属性</span><span class="sxs-lookup"><span data-stu-id="725f8-109">Attributes</span></span>](../../../docs/standard/design-guidelines/attributes.md)  
 [<span data-ttu-id="725f8-110">コレクション</span><span class="sxs-lookup"><span data-stu-id="725f8-110">Collections</span></span>](/cpp/mfc/collections)  
 [<span data-ttu-id="725f8-111">シリアル化</span><span class="sxs-lookup"><span data-stu-id="725f8-111">Serialization</span></span>](../../../docs/standard/design-guidelines/serialization.md)  
 [<span data-ttu-id="725f8-112">System.Xml の使用法</span><span class="sxs-lookup"><span data-stu-id="725f8-112">System.Xml Usage</span></span>](../../../docs/standard/design-guidelines/system-xml-usage.md)  
 [<span data-ttu-id="725f8-113">等値演算子</span><span class="sxs-lookup"><span data-stu-id="725f8-113">Equality Operators</span></span>](../../../docs/standard/design-guidelines/equality-operators.md)  
 <span data-ttu-id="725f8-114">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="725f8-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="725f8-115">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="725f8-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="725f8-116">参照</span><span class="sxs-lookup"><span data-stu-id="725f8-116">See Also</span></span>  
 [<span data-ttu-id="725f8-117">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="725f8-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
