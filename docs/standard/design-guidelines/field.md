---
title: "フィールドのデザイン"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ccced2c9e816122d770f43056c36ab4a6d510fde
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="field-design"></a><span data-ttu-id="1e8d9-102">フィールドのデザイン</span><span class="sxs-lookup"><span data-stu-id="1e8d9-102">Field Design</span></span>
<span data-ttu-id="1e8d9-103">カプセル化の原則が、最も重要な概念のいずれかのオブジェクト指向デザインします。</span><span class="sxs-lookup"><span data-stu-id="1e8d9-103">The principle of encapsulation is one of the most important notions in object-oriented design.</span></span> <span data-ttu-id="1e8d9-104">この原則は、オブジェクト内に格納されているデータはそのオブジェクトにのみアクセスできることを示します。</span><span class="sxs-lookup"><span data-stu-id="1e8d9-104">This principle states that data stored inside an object should be accessible only to that object.</span></span>  
  
 <span data-ttu-id="1e8d9-105">原則を解釈する便利な方法は、言い換えれば、その型 (名前やタイプの変更) のフィールドへの変更が、型のメンバーを以外のコードを変更せずにできるように、型を設計することができます。</span><span class="sxs-lookup"><span data-stu-id="1e8d9-105">A useful way to interpret the principle is to say that a type should be designed so that changes to fields of that type (name or type changes) can be made without breaking code other than for members of the type.</span></span> <span data-ttu-id="1e8d9-106">この解釈は、すぐに、すべてのフィールドをプライベートでなければならないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="1e8d9-106">This interpretation immediately implies that all fields must be private.</span></span>  
  
 <span data-ttu-id="1e8d9-107">この厳密な制限から定数と静的な読み取り専用のフィールドは必要であるため、このようなフィールドほぼ定義では、決してを変更するお除外します。</span><span class="sxs-lookup"><span data-stu-id="1e8d9-107">We exclude constant and static read-only fields from this strict restriction, because such fields, almost by definition, are never required to change.</span></span>  
  
 <span data-ttu-id="1e8d9-108">**X しないで**パブリックまたは保護されたインスタンス フィールドを提供します。</span><span class="sxs-lookup"><span data-stu-id="1e8d9-108">**X DO NOT** provide instance fields that are public or protected.</span></span>  
  
 <span data-ttu-id="1e8d9-109">Public または protected ようにではなくフィールドにアクセスするため、プロパティを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e8d9-109">You should provide properties for accessing fields instead of making them public or protected.</span></span>  
  
 <span data-ttu-id="1e8d9-110">**✓ しないで**は決して変化しない定数の定数フィールドを使用します。</span><span class="sxs-lookup"><span data-stu-id="1e8d9-110">**✓ DO** use constant fields for constants that will never change.</span></span>  
  
 <span data-ttu-id="1e8d9-111">コンパイラは、コードの呼び出しに直接 const フィールドの値を書き込みますがします。</span><span class="sxs-lookup"><span data-stu-id="1e8d9-111">The compiler burns the values of const fields directly into calling code.</span></span> <span data-ttu-id="1e8d9-112">そのため、const の値は変更不可能互換性の問題の危険を回避します。</span><span class="sxs-lookup"><span data-stu-id="1e8d9-112">Therefore, const values can never be changed without the risk of breaking compatibility.</span></span>  
  
 <span data-ttu-id="1e8d9-113">**✓ しないで**のパブリック静的を使用して`readonly`フィールドの定義済みのオブジェクト インスタンス。</span><span class="sxs-lookup"><span data-stu-id="1e8d9-113">**✓ DO** use public static `readonly` fields for predefined object instances.</span></span>  
  
 <span data-ttu-id="1e8d9-114">型の定義済みのインスタンスが場合、により読み取り専用で、型自体の静的フィールドをパブリックとしてと宣言します。</span><span class="sxs-lookup"><span data-stu-id="1e8d9-114">If there are predefined instances of the type, declare them as public read-only static fields of the type itself.</span></span>  
  
 <span data-ttu-id="1e8d9-115">**X しないで**への変更可能な型のインスタンスを割り当てる`readonly`フィールドです。</span><span class="sxs-lookup"><span data-stu-id="1e8d9-115">**X DO NOT** assign instances of mutable types to `readonly` fields.</span></span>  
  
 <span data-ttu-id="1e8d9-116">変更可能な型は、インスタンスは作成後に変更することができますのインスタンスを持つ型です。</span><span class="sxs-lookup"><span data-stu-id="1e8d9-116">A mutable type is a type with instances that can be modified after they are instantiated.</span></span> <span data-ttu-id="1e8d9-117">たとえば、配列、ほとんどのコレクション、およびストリームは変更可能な型が<xref:System.Int32?displayProperty=nameWithType>、 <xref:System.Uri?displayProperty=nameWithType>、および<xref:System.String?displayProperty=nameWithType>はすべて変更できません。</span><span class="sxs-lookup"><span data-stu-id="1e8d9-117">For example, arrays, most collections, and streams are mutable types, but <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, and <xref:System.String?displayProperty=nameWithType> are all immutable.</span></span> <span data-ttu-id="1e8d9-118">参照型のフィールドで読み取り専用の修飾子には、置き換えられるのフィールドに格納されているインスタンスができなくなりますが、フィールドのインスタンス データのインスタンスを変更するメンバーを呼び出すことによって変更されているを妨げることはできません。</span><span class="sxs-lookup"><span data-stu-id="1e8d9-118">The read-only modifier on a reference type field prevents the instance stored in the field from being replaced, but it does not prevent the field’s instance data from being modified by calling members changing the instance.</span></span>  
  
 <span data-ttu-id="1e8d9-119">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="1e8d9-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="1e8d9-120">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="1e8d9-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e8d9-121">参照</span><span class="sxs-lookup"><span data-stu-id="1e8d9-121">See Also</span></span>  
 [<span data-ttu-id="1e8d9-122">メンバーのデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="1e8d9-122">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="1e8d9-123">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="1e8d9-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
