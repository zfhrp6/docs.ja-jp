---
title: ".NET での文字列の解析"
description: ".NET での文字列の解析"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/22/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 8103c0a6-61d3-40dd-a3e9-2a32ba6a4c05
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: c741ae793d491f691a355df6ad064b81d609c7e5
ms.lasthandoff: 03/03/2017

---

# <a name="parsing-strings-in-net"></a>.NET での文字列の解析

解析操作では、.NET の基本データ型を表す文字列をその基本データ型に変換します。 たとえば解析操作は、文字列を浮動小数点数や日付と時刻の値に変換するために使用します。 解析操作を実行するには、`Parse` メソッドがよく使用されます。 解析は書式設定の逆の操作 (基本データ型のその文字列形式への変換を含む) であるため、多くの同じ規則が適用されます。 カルチャに依存する書式情報を指定するために、書式設定で [IFormatProvider](xref:System.IFormatProvider) インターフェイスを実装するオブジェクトを使用するのと同じように、解析でも [IFormatProvider](xref:System.IFormatProvider) インターフェイスを実装するオブジェクトを使用し、文字列形式を解釈する方法を決定します。 詳細については、「[.NET での型の書式設定](formatting-types.md)」をご覧ください。

## <a name="in-this-section"></a>このセクションの内容

[.NET での数値文字列の解析](parsing-numeric.md) - 文字列を .NET の数値文字列に変換する方法について説明します。

[.NET での日付と時刻文字列の解析](parsing-datetime.md) - 文字列を .NET の `DateTime` 型に変換する方法について説明します。

[.NET でのその他の文字列の解析](parsing-other.md) - 文字列を [Char](xref:System.Char)、[Boolean](xref:System.Boolean)、および [Enum](xref:System.Enum) 型に変換する方法について説明します。

[.NET での型の書式設定](formatting-types.md) - 書式指定子および書式プロバイダーなどの基本書式の概念について説明します。

[.NET での型変換](type-conversion.md) - 型を変換する方法について説明します。

[.NET での基本データ型の操作](index.md) - .NET の基本データ型で実行できる一般的な操作について説明します。


