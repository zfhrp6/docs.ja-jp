---
title: "正規表現におけるスレッド セーフ"
description: "正規表現におけるスレッド セーフ"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: dc64b681-b3aa-4911-8e30-0764a8b6a852
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 6b410da1982519fd9ff137bd38f1d074ce08d39b

---

# <a name="thread-safety-in-regular-expressions"></a>正規表現におけるスレッド セーフ

[Regex](xref:System.Text.RegularExpressions.Regex) クラス自体はスレッド セーフであり、変更できません (読み取り専用)。 つまり、[Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトは任意のスレッドで作成できます。また、スレッド間で共有できます。一致するメソッドは任意のスレッドから呼び出すことができますが、グローバルな状態を変更することはできません。

ただし、[Regex](xref:System.Text.RegularExpressions.Regex) から返された結果オブジェクト ([Match](xref:System.Text.RegularExpressions.Match) と [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection)) は、単一のスレッドで使用する必要があります。 これらのオブジェクトの多くは、論理的に変更できませんが、実装によってパフォーマンスを改善するために一部の結果の演算を遅延させることができます。結果として、呼び出し側はオブジェクトに対するアクセスをシリアル化する必要があります。

複数のスレッドで [Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトを共有する必要がある場合、同期されたメソッドを呼び出すことで、それらのオブジェクトはスレッドセーフ インスタンスに変換できます。 列挙子の例外はありますが、すべての正規表現クラスはスレッド セーフです。または、同期されたメソッドでスレッドセーフ オブジェクトに変換することができます。

列挙子は唯一の例外です。 アプリケーションはコレクション列挙子に対する呼び出しをシリアル化する必要があります。 複数のスレッドでコレクションを同時に列挙できる場合、列挙子によってスキャンされるコレクションのルート オブジェクト上の列挙子メソッドを同期する必要があります。

## <a name="see-also"></a>関連項目

[.NET 正規表現](regular-expressions.md)




<!--HONumber=Nov16_HO1-->


