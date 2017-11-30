---
title: "方法: .NET Framework で基本的な文字列操作を実行する"
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
helpviewer_keywords: strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ee9c00d02b7b5d1f391ce60f843c18445efd6edc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a><span data-ttu-id="3c31b-102">方法: .NET での基本的な文字列操作の実行</span><span class="sxs-lookup"><span data-stu-id="3c31b-102">How to: Perform Basic String Manipulations in .NET</span></span>
<span data-ttu-id="3c31b-103">次の例で説明した手法のいくつか、[基本的な文字列操作](../../../docs/standard/base-types/basic-string-operations.md)実際のアプリケーションで見つかる可能性があるように文字列操作を実行するクラスを構築するためにトピックです。</span><span class="sxs-lookup"><span data-stu-id="3c31b-103">The following example uses some of the methods discussed in the [Basic String Operations](../../../docs/standard/base-types/basic-string-operations.md) topics to construct a class that performs string manipulations in a manner that might be found in a real-world application.</span></span> <span data-ttu-id="3c31b-104">`MailToData` クラスは、個人の名前とアドレスを個別のプロパティに格納し、`City`、`State`、`Zip` フィールドを組み合わせて、ユーザーに表示する1 つの文字列にする方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="3c31b-104">The `MailToData` class stores the name and address of an individual in separate properties and provides a way to combine the `City`, `State`, and `Zip` fields into a single string for display to the user.</span></span> <span data-ttu-id="3c31b-105">さらに、このクラスを使用して、ユーザーが市区町村、都道府県、および郵便番号情報を 1 つの文字列として入力することができます。アプリケーションは自動的に 1 つの文字列を解析し、対応するプロパティに適切な情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="3c31b-105">Furthermore, the class allows the user to enter the city, state, and ZIP Code information as a single string; the application automatically parses the single string and enters the proper information into the corresponding property.</span></span>  
  
 <span data-ttu-id="3c31b-106">わかりやすいように、この例ではコマンド ライン インターフェイスによるコンソール アプリケーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="3c31b-106">For simplicity, this example uses a console application with a command-line interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c31b-107">例</span><span class="sxs-lookup"><span data-stu-id="3c31b-107">Example</span></span>  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 <span data-ttu-id="3c31b-108">上記のコードを実行すると、ユーザーは自分の名前とアドレスを入力するように求められます。</span><span class="sxs-lookup"><span data-stu-id="3c31b-108">When the preceding code is executed, the user is asked to enter his or her name and address.</span></span> <span data-ttu-id="3c31b-109">アプリケーションは、適切なプロパティに情報を格納し、市区町村、都道府県、および郵便番号情報を表示する 1 つの文字列を作成して、ユーザーに情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="3c31b-109">The application places the information in the appropriate properties and displays the information back to the user, creating a single string that displays the city, state, and ZIP Code information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c31b-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c31b-110">See Also</span></span>  
 [<span data-ttu-id="3c31b-111">基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="3c31b-111">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
