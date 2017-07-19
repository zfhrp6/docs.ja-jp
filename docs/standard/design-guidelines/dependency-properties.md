---
title: "依存関係プロパティ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
caps.latest.revision: 4
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 4
---
# 依存関係プロパティ
依存関係プロパティ \(DP\) は、たとえば、型の変数 \(フィールド\) に格納することではなくプロパティ ストア内の値を格納する標準プロパティです。  
  
 割り当てられた依存プロパティは、オブジェクトとそのコンテナーの間のリレーションシップを記述する「プロパティ」を表す、Get および Set の静的メソッドとしてモデル化された依存関係プロパティの種類 \(の位置など、 `Button` 上のオブジェクト、 `Panel` コンテナー\) です。  
  
 **✓ は** プロパティをスタイル設定、トリガー、データ バインディング、アニメーション、動的リソース、および継承などの WPF 機能をサポートする必要がある場合は、依存関係プロパティを提供します。  
  
## 依存関係プロパティのデザイン  
 **✓ は** から継承 <xref:System.Windows.DependencyObject>, 、または依存関係プロパティを実装する場合、そのサブタイプのいずれかです。 種類は、プロパティ ストアの非常に効率的な実装を提供し、自動的に WPF データ バインドをサポートします。  
  
 **✓ は** は、通常の CLR プロパティとパブリック静的な読み取り専用フィールドのインスタンスを格納する指定 <xref:System.Windows.DependencyProperty?displayProperty=fullName> 各依存関係プロパティ。  
  
 **✓ は** インスタンス メソッドを呼び出すことによって依存関係プロパティを実装する <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=fullName> と <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=fullName>です。  
  
 **✓ は** "Property"を使用してプロパティの名前をアスタリスクの依存関係プロパティの静的フィールドの名前  
  
 **X のしないで** 代わりにメタデータの設定は、コード内の依存関係プロパティの既定値を明示的に設定します。  
  
 プロパティの既定値を明示的に設定すると、スタイルなどのなんらかの暗黙的な方法で設定されているからそのプロパティをできない場合があります。  
  
 **X のしないで** 静的フィールドにアクセスする標準的なコード以外のプロパティ アクセサーにコードを追加します。  
  
 静的フィールドを直接使用することはありませんとコードが実行プロパティ、スタイルなどの暗黙的な方法でスタイル処理のためです。  
  
 **X のしないで** 依存関係プロパティを使用してセキュリティで保護されたデータを格納します。 でもプライベート依存関係プロパティは、パブリックにアクセスできます。  
  
## 接続されている依存関係プロパティのデザイン  
 前のセクションで説明されている依存関係プロパティは宣言型の組み込みのプロパティを表しますたとえば、 `Text` プロパティは、プロパティの `TextButton`, 、それを宣言します。 特殊な依存関係プロパティは、接続されている依存関係プロパティです。  
  
 添付プロパティの典型的な例は、 <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=fullName> プロパティです。 プロパティ ボタン \(いないグリッドの\) 列の位置を表すは、「その」ボタンをグリッドで、グリッドで、ボタンが含まれている場合にのみ該当します。  
  
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
  
 添付プロパティの定義は、アクセサーが静的の Get と Set メソッドで表されること以外に、通常の依存関係プロパティのほとんどの場合ようになります。  
  
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
  
## 依存関係プロパティの検証  
 プロパティは、多くの場合、検証と呼ばれるものを実装します。 プロパティの値を変更しようとは、検証ロジックを実行します。  
  
 残念なことに依存関係プロパティ アクセサーの場合は、任意の検証コードを含めることはできません。 代わりに、依存関係プロパティの検証ロジックは、プロパティの登録時に指定する必要があります。  
  
 **X のしないで** プロパティのアクセサーの依存関係プロパティの検証ロジックを配置します。 代わりに、検証コールバックを渡す `DependencyProperty.Register` メソッドです。  
  
## 依存関係プロパティの変更通知  
 **X のしないで** 依存関係プロパティのアクセサーで変更通知のロジックを実装します。 依存関係プロパティには、変更通知のコールバックを指定する必要がある組み込みの変更通知機能があり、 <xref:System.Windows.PropertyMetadata>です。  
  
## 依存関係プロパティの値の強制型変換  
 プロパティ ストアが実際に変更される前に、set アクセス操作子、プロパティ set アクセス操作子に渡された値が変更されたときにプロパティの強制型変換が行われます。  
  
 **X のしないで** 依存関係プロパティのアクセサーに強制変換ロジックを実装します。  
  
 依存関係プロパティが、組み込みの強制型変換機能を持っているし、強制型変換のコールバックを指定することで使用できます、 `PropertyMetadata`です。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)   
 [一般的な設計パターン](../../../docs/standard/design-guidelines/common-design-patterns.md)