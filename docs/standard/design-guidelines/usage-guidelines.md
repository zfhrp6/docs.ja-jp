---
title: 使用方法のガイドライン
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 02905c193387f78430ce1885449055060d07bf82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571034"
---
# <a name="usage-guidelines"></a><span data-ttu-id="b332e-102">使用方法のガイドライン</span><span class="sxs-lookup"><span data-stu-id="b332e-102">Usage Guidelines</span></span>
<span data-ttu-id="b332e-103">このセクションには、パブリックにアクセスできる Api の一般的な種類の使用に関するガイドラインが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b332e-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="b332e-104">組み込みフレームワーク型 (シリアル化属性など) および一般的な演算子をオーバー ロードの直接の使用状況を処理します。</span><span class="sxs-lookup"><span data-stu-id="b332e-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>  
  
 <span data-ttu-id="b332e-105"><xref:System.IDisposable?displayProperty=nameWithType>インターフェイスは、このセクションでは説明しませんが、については、 [Dispose パターン](../../../docs/standard/design-guidelines/dispose-pattern.md)セクションです。</span><span class="sxs-lookup"><span data-stu-id="b332e-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../../../docs/standard/design-guidelines/dispose-pattern.md) section.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b332e-106">ガイドラインとその他の一般的なに関する追加情報、組み込みの .NET Framework 型を参照してください、次の参照トピック: <xref:System.DateTime?displayProperty=nameWithType>、 <xref:System.DateTimeOffset?displayProperty=nameWithType>、 <xref:System.ICloneable?displayProperty=nameWithType>、 <xref:System.IComparable%601?displayProperty=nameWithType>、 <xref:System.IEquatable%601?displayProperty=nameWithType>、 <xref:System.Nullable%601?displayProperty=nameWithType>、 <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b332e-106">For guidelines and additional information about about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b332e-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b332e-107">In This Section</span></span>  
 [<span data-ttu-id="b332e-108">配列</span><span class="sxs-lookup"><span data-stu-id="b332e-108">Arrays</span></span>](../../../docs/standard/design-guidelines/arrays.md)  
 [<span data-ttu-id="b332e-109">属性</span><span class="sxs-lookup"><span data-stu-id="b332e-109">Attributes</span></span>](../../../docs/standard/design-guidelines/attributes.md)  
 [<span data-ttu-id="b332e-110">コレクション</span><span class="sxs-lookup"><span data-stu-id="b332e-110">Collections</span></span>](/cpp/mfc/collections)  
 [<span data-ttu-id="b332e-111">シリアル化</span><span class="sxs-lookup"><span data-stu-id="b332e-111">Serialization</span></span>](../../../docs/standard/design-guidelines/serialization.md)  
 [<span data-ttu-id="b332e-112">System.Xml の使用法</span><span class="sxs-lookup"><span data-stu-id="b332e-112">System.Xml Usage</span></span>](../../../docs/standard/design-guidelines/system-xml-usage.md)  
 [<span data-ttu-id="b332e-113">等値演算子</span><span class="sxs-lookup"><span data-stu-id="b332e-113">Equality Operators</span></span>](../../../docs/standard/design-guidelines/equality-operators.md)  
 <span data-ttu-id="b332e-114">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="b332e-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b332e-115">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="b332e-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b332e-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="b332e-116">See Also</span></span>  
 [<span data-ttu-id="b332e-117">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="b332e-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
