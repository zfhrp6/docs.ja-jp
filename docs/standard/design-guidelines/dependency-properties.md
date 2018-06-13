---
title: 依存関係プロパティ
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 039015f895a491d8709815d6aff52eb6139d779f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576117"
---
# <a name="dependency-properties"></a>依存関係プロパティ
依存関係プロパティ (DP) は、たとえば (フィールド) の型の変数に保存することではなく、プロパティ ストア内の値を格納する標準プロパティです。  
  
 割り当てられた依存プロパティはオブジェクトとそのコンテナーの間のリレーションシップを記述する「プロパティ」を表す、Get および Set の静的メソッドとしてモデル化された依存関係プロパティの種類 (の位置など、`Button`上のオブジェクト、 `Panel`コンテナー) です。  
  
 **✓ しないで**プロパティ スタイル設定、トリガー、データ バインディング、アニメーション、動的なリソース、および継承などの WPF 機能をサポートする必要がある場合は、依存関係プロパティを提供します。  
  
## <a name="dependency-property-design"></a>依存関係プロパティのデザイン  
 **✓ しないで**から継承<xref:System.Windows.DependencyObject>、または依存関係プロパティを実装する場合、そのサブタイプのいずれか。 種類は、プロパティ ストアの非常に効率的な実装を提供し、自動的に WPF データ バインディングをサポートします。  
  
 **✓ しないで**正規の CLR プロパティとパブリックな静的読み取り専用フィールドのインスタンスを格納する提供<xref:System.Windows.DependencyProperty?displayProperty=nameWithType>各依存関係プロパティです。  
  
 **✓ しないで**依存関係プロパティを実装するインスタンス メソッドを呼び出すことによって<xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType>と<xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>です。  
  
 **✓ しないで**"Property"のプロパティの名前をアスタリスクの依存関係プロパティの静的フィールドの名前  
  
 **X しないで**コード内の依存関係プロパティの既定値を明示的に設定を代わりにメタデータの設定です。  
  
 プロパティの既定値を明示的に設定するから、スタイルなどのいくつかの暗黙的な方法で設定されているそのプロパティをできない場合があります。  
  
 **X しないで**静的フィールドにアクセスする標準コード以外のプロパティ アクセサーにコードを配置します。  
  
 静的フィールドを直接使用するコードはありませんは実行、スタイルなどの暗黙的な方法で、プロパティが設定されている場合のスタイルを設定するためです。  
  
 **X しないで**依存関係プロパティを使用してセキュリティで保護されたデータを格納します。 さらにプライベート依存関係プロパティをパブリックにアクセスすることができます。  
  
## <a name="attached-dependency-property-design"></a>接続されている依存関係プロパティのデザイン  
 前のセクションで説明されている依存関係プロパティの宣言する型の組み込みのプロパティを表しますたとえば、`Text`プロパティは、プロパティの`TextButton`を宣言しています。 依存関係プロパティの特別な種類は、接続されている依存関係プロパティです。  
  
 添付プロパティの典型的な例は、<xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType>プロパティです。 プロパティ ボタン (いないグリッドの) 列の位置を表すは"にアタッチされて"ボタン グリッドで、グリッドで、ボタンが含まれている場合にのみ関連します。  
  
```  
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
  
    <Button Grid.Column="0">Click</Button>  
    <Button Grid.Column="1">Clack</Button>  
</Grid>  
```  
  
 添付プロパティの定義は、アクセサーが静的の Get および Set メソッドによって表される点を除いて、ほとんどの場合と同様に、通常の依存関係プロパティの検索します。  
  
```  
public class Grid {  
  
    public static int GetColumn(DependencyObject obj) {  
        return (int)obj.GetValue(ColumnProperty);  
    }  
  
    public static void SetColumn(DependencyObject obj, int value) {  
        obj.SetValue(ColumnProperty,value);  
    }  
  
    public static readonly DependencyProperty ColumnProperty =  
        DependencyProperty.RegisterAttached(  
            "Column",  
            typeof(int),  
            typeof(Grid)  
    );  
}  
```  
  
## <a name="dependency-property-validation"></a>依存関係プロパティの検証  
 プロパティは、多くの場合、検証と呼ばれるものを実装します。 プロパティの値を変更する試みが行われたときに検証ロジックを実行します。  
  
 残念なことに依存関係プロパティのアクセサーでは、任意の検証コードを含めることはできません。 代わりに、依存関係プロパティの検証ロジックは、プロパティの登録中に指定する必要があります。  
  
 **X しないで**プロパティのアクセサーの依存関係プロパティの検証ロジックを配置します。 代わりに、検証コールバックを渡す`DependencyProperty.Register`メソッドです。  
  
## <a name="dependency-property-change-notifications"></a>依存関係プロパティの変更通知  
 **X しないで**依存関係プロパティのアクセサーでの変更通知のロジックを実装します。 依存関係プロパティを変更通知のコールバックを指定することによって処理するために使用する必要があります組み込みの変更通知機能があり、<xref:System.Windows.PropertyMetadata>です。  
  
## <a name="dependency-property-value-coercion"></a>依存関係プロパティの値の強制  
 プロパティの強制変換は、プロパティ ストアが実際に変更する前に、set アクセス操作子がプロパティ set アクセス操作子に渡された値が変更されたときに行われます。  
  
 **X しないで**依存関係プロパティのアクセサーに強制変換ロジックを実装します。  
  
 依存関係プロパティが、ビルトインの強制変換機能を持っているし、強制型変換のコールバックを指定することによって使用できます、`PropertyMetadata`です。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [共通デザイン パターン](../../../docs/standard/design-guidelines/common-design-patterns.md)
