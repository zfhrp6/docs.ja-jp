---
title: "方法: .NET 標準オブジェクトがシリアル化可能なかどうかを判断します。"
description: "実行時に、標準の .NET 型をシリアル化できるかどうかを確認する方法を示します。"
ms.custom: 
ms.date: 10/20/2017
ms.prod: .net
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7c44e350ad4e561f03bf6c598172058a0a9ca41e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a>方法: .NET 標準オブジェクトがシリアル化可能なかどうかを判断します。

.NET 標準は、型とそのバージョンの標準に準拠している特定の .NET 実装上に存在する必要があるメンバーを定義する仕様です。 ただし、.NET 標準定義しません、型がシリアル化できるかどうか。 .NET 標準ライブラリで定義された型がでマークされていない、<xref:System.SerializableAttribute>属性。 代わりに、.NET Core と .NET Framework などの特定の .NET 実装は、特定の型がシリアル化できるかどうかを判断するために解放します。 

対象とする .NET 標準のライブラリを開発した場合は、.NET 標準をサポートする .NET の実装によって、ライブラリを使用できます。 つまり、ことはできませんがわかっている事前に特定の型がシリアル化できるかどうかのみ、実行時にシリアル化可能なことがあるかどうかを判断できます。

値を取得することによって、オブジェクトが実行時にシリアル化可能かどうかを判断できます、<xref:System.Type.IsSerializable>のプロパティ、<xref:System.Type>そのオブジェクトの型を表すオブジェクト。 次の例では、1 つの実装を提供します。 定義する、`IsSerializable(Object)`拡張メソッドを示すかどうか、<xref:System.Object>インスタンスをシリアル化することができます。

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

かどうかをシリアル化して、次の例として、現在の .NET 実装に逆シリアル化を決定する方法を任意のオブジェクトを渡すことができますし、します。

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

# <a name="see-also"></a>関連項目

[バイナリ シリアル化](binary-serialization.md)   
<xref:System.SerializableAttribute?displayProperty=fullName>    
<xref:System.Type.IsSerializable?displayProperty=nameWithType>   
