---
title: ".NET 標準の新機能"
ms.custom: updateeachrelease
ms.date: 11/08/2017
ms.prod: .net
ms.topic: article
ms.technology: dotnet-standard
ms.##devlang: dotnet
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e938c009b79af3b2f36094bbb74f4d38baeeac0b
ms.sourcegitcommit: 281070dee88db86ec3bb4634d5f558d1a4e159dd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2017
---
# <a name="whats-new-in-the-net-standard"></a>.NET 標準の新機能

.NET 標準は、そのバージョンの標準に準拠している .NET の実装で使用できる必要がありますのある Api のバージョン管理されたセットを定義する正式な仕様です。 .NET Standard はライブラリ開発者を対象としています。 .NET 標準バージョンを対象とするライブラリは、そのバージョンの標準をサポートする任意の .NET Framework、.NET Core または Xamarin 実装で使用できます。

.NET 標準の最新バージョンは 2.0 です。 インストールされている、.NET Core のワークロードで、.NET Core 2.0 SDK、および Visual Studio 2017 バージョン 15.3 に含まれます。

## <a name="supported-net-implementations"></a>サポートされている .NET の実装

標準の .NET 2.0 は、次の .NET の実装によってサポートされます。

- .NET core 2.0
- .NET Framework 4.6.1
- モノラル 5.4
- Xamarin.iOS 10.14
- Xamarin.Mac 3.8
- Xamarin.Android 8.0
- ユニバーサル Windows プラットフォーム 10.0.16299

## <a name="whats-new-in-the-net-standard-20"></a>標準の .NET 2.0 の新機能
 
標準の .NET 2.0 には、次の新機能が含まれています。

**大幅に拡張された一連の Api**

バージョン 1.6、を介して .NET 標準は、Api の比較的小さなサブセットを含めます。 除外される間、.NET Framework または Xamarin でよく使用されていた Api の多くが発生しました。 これは、アプリケーションと .NET の複数の実装を対象とするライブラリを開発するときに、開発者が使い慣れた Api の適切な代替を見つけることが必要なために、開発は複雑になります。 標準の .NET 2.0 では、.NET 標準 1.6、標準の以前のバージョンで使用できたより以上 20,000 以上の Api を追加することでこの制限を説明します。 標準の .NET 2.0 に追加されている Api の一覧は、次を参照してください。 [.NET 標準 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md)です。 

いくつかの追加機能を<xref:System>.NET 規格 2.0 で名前空間が含まれます。

- サポート、<xref:System.AppDomain>クラスです。
- 配列内の他のメンバーからの操作のサポートの向上、<xref:System.Array>クラスです。
- 属性の追加メンバーを操作するためのサポートが強化、<xref:System.Attribute>クラスです。
- サポートおよびの追加の書式設定オプションをより深くカレンダー<xref:System.DateTime>値。
- 追加<xref:System.Decimal>機能の丸め処理を行います。
- 追加の機能、<xref:System.Environment>クラスです。
- ガベージ コレクターを制御を強化、<xref:System.GC>クラスです。
- 文字列比較、列挙、および正規化の拡張サポートを<xref:System.String>クラスです。
- 夏時間の調整と遷移の時刻のサポート、<xref:System.TimeZoneInfo.AdjustmentRule>と<xref:System.TimeZoneInfo.TransitionTime>クラスです。
- 機能を大幅に強化されて、<xref:System.Type>クラスです。
- 例外のコンス トラクターを追加することによって例外オブジェクトの逆シリアル化のサポートの向上<xref:System.Runtime.Serialization.SerializationInfo>と<xref:System.Runtime.Serialization.StreamingContext>パラメーター。

**.NET Framework ライブラリのサポート**

.NET Framework はなく、標準の .NET ライブラリの圧倒的を対象します。 ただし、これらのライブラリでの呼び出しのほとんどは、標準の .NET 2.0 に含まれる Api には。 標準の .NET 2.0 から始めてからアクセスできます .NET Framework ライブラリ、標準の .NET ライブラリを使用して、[互換性 shim](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification)です。 この互換性レイヤーが開発者; に対して透過的です。.NET Framework ライブラリを活用するために何もする必要はありません。

1 つの要件は、標準 .NET 2.0 では、.NET Framework クラス ライブラリによって呼び出される Api を含める必要があることです。

**Visual Basic のサポート**

Visual Basic で標準の .NET ライブラリを開発できます。 Visual Studio 2017 バージョン 15.3 を使用している Visual Basic 開発者、またはインストールされている、.NET Core のワークロードで後では、Visual Studio には今すぐ .NET 標準的なクラス ライブラリ テンプレートが含まれます。 その他の開発ツールや環境を使用している Visual Basic 開発者は、使用することができます、 [dotnet 新しい](../../core/tools/dotnet-new.md).NET 標準ライブラリ プロジェクトを作成するコマンド。 詳細については、次を参照してください。、 [.NET 標準ライブラリ用ツール サポート](#tooling)です。

<a name="tooling" />**.NET 標準ライブラリ用ツール サポート**

.NET Core 2.0 と .NET 標準 2.0、Visual Studio 2017 年両方のリリースでは、 [.NET Core コマンド ライン インターフェイス (CLI)](../../core/tools/index.md) .NET 標準ライブラリの作成用ツール サポートが含まれます。 

Visual Studio をインストールする場合、 **.NET Core クロスプラット フォーム開発**ワークロードをプロジェクト テンプレートを使用して、次の図に示すとして .NET 標準 2.0 ライブラリ プロジェクトを作成することができます。 

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
![新しい .NET 標準のライブラリ プロジェクトに追加します。](./media/std-project-cs.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
<a name="add-new-net-standard-library-projectmediastd-project-vbpng"></a>![新しい .NET 標準のライブラリ プロジェクトに追加します。](./media/std-project-vb.png)
---

使用するかどうかは、次の .NET Core CLI [dotnet 新しい](../../core/tools/dotnet-new.md)コマンドは、標準の .NET 2.0 を対象とするクラス ライブラリ プロジェクトを作成します。

```csharp
dotnet new classlib
```
```vb
dotnet new classlib -lang vb
```
  
## <a name="see-also"></a>関連項目
[.NET 標準](../net-standard.md)
[.NET 標準の概要](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)
