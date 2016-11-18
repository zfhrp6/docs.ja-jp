---
title: "方法: コンピューター上に存在するタイム ゾーンを列挙する"
description: "方法: コンピューター上に存在するタイム ゾーンを列挙する"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: c5ae4a6c-1790-4355-b5b1-879aaf956129
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: 5f385636137777013b540e8c1233751624139859

---

# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>方法: コンピューター上に存在するタイム ゾーンを列挙する

指定されたタイム ゾーンを正しく処理するには、そのタイム ゾーンに関する情報がシステムで使用できる必要があります。 たとえば、Windows オペレーティング システムでは、この情報はレジストリに格納されます。 しかし、世界中に存在するタイム ゾーンの合計数は大きいものの、レジストリにはそれらの一部に関する情報しか含まれません。 さらに、レジストリ自体は、内容が意図的に、および誤って変更される可能性がある動的な構造です。 その結果、アプリケーションは、特定のタイム ゾーンがシステムで定義され、使用できると常に想定することができません。 タイム ゾーン情報のアプリケーションを使用する多くのアプリケーションの最初の手順は、必要なタイム ゾーンがローカル システムで使用できるかどうかを判断する、またはタイム ゾーンの一覧をユーザーに提供して選択させることです。 これには、アプリケーションがローカル システムで定義されているタイム ゾーンを列挙する必要があります。 

## <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>ローカル システムに存在するタイム ゾーンを列挙するには

1. [TimeZoneInfo.GetSystemTimeZones](xref:System.TimeZoneInfo.GetSystemTimeZones) メソッドを呼び出します。 メソッドは [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトのジェネリック [ReadOnlyCollection&lt;T&gt;](xref:System.Collections.ObjectModel.ReadOnlyCollection%601) コレクションを返します。 コレクション内のエントリは、[DisplayName](xref:System.TimeZoneInfo.DisplayName) プロパティによって並べ替えられます。 例:

    ```csharp
    ReadOnlyCollection<TimeZoneInfo> tzCollection;
    tzCollection = TimeZoneInfo.GetSystemTimeZones();
    ```

    ```vb
    Dim tzCollection As ReadOnlyCollection(Of TimeZoneInfo) = TimeZoneInfo.GetSystemTimeZones
    ```

2. `foreach` ループ (C#) または `For Each…Next` ループ (Visual Basic) を使用して、コレクション内の個々の [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトを列挙し、各オブジェクトに対して必要な処理を実行します。 たとえば、次のコードは、ステップ 1 で返された [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトの [ReadOnlyCollection&lt;T&gt;](xref:System.Collections.ObjectModel.ReadOnlyCollection%601) コレクションを列挙し、各タイム ゾーンの表示名をコンソールに一覧表示します。

    ```csharp
    foreach (TimeZoneInfo timeZone in tzCollection)
    Console.WriteLine("   {0}: {1}", timeZone.Id, timeZone.DisplayName);
    ```

    ```vb
    For Each timeZone As TimeZoneInfo In tzCollection
        Console.WriteLine("   {0}: {1}", timeZone.Id, timeZone.DisplayName)
    Next
    ```

## <a name="see-also"></a>関連項目

[日付、時刻およびタイム ゾーン](index.md)

[ローカル システムで定義されているタイム ゾーンの検索](finding-the-time-zones-on-local-system.md)




<!--HONumber=Nov16_HO3-->


