---
title: ".NET Framework クラス ライブラリの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET Framework クラス ライブラリ, 概要"
  - ".NET Framework, クラス ライブラリ"
  - "基本型, クラス ライブラリ"
  - "組み込み型"
  - "クラス ライブラリ [.NET Framework]"
  - "クラス オブジェクト値型"
  - "クラス [.NET Framework], ライブラリ概要"
  - "CLS"
  - "共通言語仕様"
  - "データ型 [.NET Framework]"
  - "データ型 [.NET Framework], C#"
  - "データ型 [.NET Framework], C++"
  - "データ型 [.NET Framework], JScript"
  - "データ型 [.NET Framework], Visual Basic"
  - "浮動小数点値型"
  - "整数値型"
  - "JScript, データ型"
  - "ライブラリ, .NET Framework クラス ライブラリ"
  - "論理値型"
  - "メンバー [.NET Framework], 型"
  - "名前空間 [.NET Framework]"
  - "名前空間 [.NET Framework], 名前空間の概要"
  - "名前付け規則 [.NET Framework]"
  - "System 名前空間"
  - "型システム [.NET Framework]"
  - "型, .NET Framework"
  - "ユーザー定義型"
  - "値型"
  - "Visual Basic, データ型"
  - "Visual C#, データ型"
  - "Visual C++, データ型"
ms.assetid: 7e4c5921-955d-4b06-8709-101873acf157
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# .NET Framework クラス ライブラリの概要
[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] には、開発プロセスを高速化および最適化し、システム機能へのアクセスを提供する、クラス、インターフェイス、および値型があります。  言語間での相互運用性を確保するために、.NET Framework のほとんどの型は共通言語仕様 \(CLS: Common Language Specification\) に準拠しています。このため、コンパイラが CLS に準拠しているすべてのプログラミング言語でこれらの型を使用できます。  
  
 .NET Framework の型は、.NET アプリケーション、.NET コンポーネント、および .NET コントロールを構築するときの基礎となります。  [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] には、次の機能を実行する型が用意されています。  
  
-   基本データ型と例外を表す。  
  
-   データ構造をカプセル化する。  
  
-   入出力を実行する。  
  
-   読み込まれた型についての情報にアクセスする。  
  
-   .NET Framework セキュリティ チェックを呼び出す。  
  
-   データ アクセス、豊富なクライアント側 GUI、およびサーバー制御式のクライアント側 GUI を提供する。  
  
 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] には、豊富なインターフェイスのセットに加えて、抽象クラスと具象 \(抽象ではない\) クラスが用意されています。  具象クラスはそのまま使用できますが、多くの場合は、具象クラスから独自のクラスを派生させます。  インターフェイスの機能を使用するには、インターフェイスを実装するクラスを作成するか、またはインターフェイスを実装する .NET Framework クラスの 1 つからクラスを派生させます。  
  
## 名前付け規則  
 .NET Framework の型では、階層構造を伴うドット構文の名前付け方法が使われます。  この方法では、関連する型が名前空間にグループ化されるため、検索と参照を簡単に行うことができます。  フルネームのうち右端のドットまでの最初の部分は、名前空間の名前です。  名前の最後の部分は型名です。  たとえば、**System.Collections.ArrayList** は **ArrayList** 型であり、名前空間 **System.Collections** に属します。  **System.Collections** 内の型を使用することで、オブジェクトのコレクションを操作できます。  
  
 この名前付け方法によって、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] を拡張するライブラリ開発者は、型の階層構造のグループを簡単に作成し、一貫性のあるわかりやすい名前を付けることができます。  また、型の完全名 \(つまり名前空間と型名\) によって型を明確に特定できるため、型名の競合を防ぐことができます。  ライブラリ開発者は、次の規則に従って名前空間の名前を付けてください。  
  
 *CompanyName*.*TechnologyName*  
  
 たとえば、名前空間 Microsoft.Word はこのガイドラインに従っています。  
  
 名前付けパターンを使用して関連する型を名前空間にグループ化する方法は、クラス ライブラリを構築および文書化するのに便利です。  ただし、この名前付け方法は、参照可能範囲、メンバー アクセス、継承、セキュリティ、バインディングには影響しません。  名前空間は複数のアセンブリにまたがって分割でき、また 1 つのアセンブリに複数の名前空間からの型を含めることができます。  アセンブリは、共通言語ランタイムにおけるバージョン管理、配置、セキュリティ、読み込み、および参照可能範囲のための構造を提供します。  
  
 名前空間と型の名前の詳細については、「[共通型システム](../../docs/standard/base-types/common-type-system.md)」を参照してください。  
  
## 名前空間 System  
 <xref:System> 名前空間は、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] における基本的な型のルート名前空間です。  この名前空間には、<xref:System.Object> \(継承階層構造のルート\)、<xref:System.Byte>、<xref:System.Char>、<xref:System.Array>、<xref:System.Int32>、<xref:System.String> など、すべてのアプリケーションで使用される基本データ型を表すクラスが含まれます。  これらの型の多くは、プログラミング言語で使われるプリミティブなデータ型に対応します。  .NET Framework の型を使用してコードを記述するときには、.NET Framework の基本データ型が使用されるところに、プログラミング言語側の対応するキーワードを使用できます。  
  
 次の表では、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] に用意されているそれぞれの基本型の一覧を示し、各型について簡単に説明し、Visual Basic、C\#、C\+\+、JScript での対応する型を示します。  
  
|カテゴリ|クラス名|説明|Visual Basic のデータ型|C\# のデータ型|C\+\+ データ型|JScript のデータ型|  
|----------|----------|--------|------------------------|---------------|----------------|-------------------|  
|整数|<xref:System.Byte>|8 ビット符号なし整数。|**Byte**|**byte**|**unsigned char**|**Byte**|  
||<xref:System.SByte>|8 ビット符号付き整数。<br /><br /> 非 CLS 準拠|**SByte**|**sbyte**|**char**<br /><br /> または<br /><br /> **signed** **char**|**SByte**|  
||<xref:System.Int16>|16 ビット符号付き整数。|**Short**|**short**|**short**|**short**|  
||<xref:System.Int32>|32 ビット符号付き整数。|**整数**|**int**|**int**<br /><br /> または<br /><br /> **long**|**int**|  
||<xref:System.Int64>|64 ビット符号付き整数|**Long**|**long**|**\_\_int64**|**long**|  
||<xref:System.UInt16>|16 ビット符号なし整数。<br /><br /> 非 CLS 準拠|**UShort**|**ushort**|**unsigned short**|**UInt16**|  
||<xref:System.UInt32>|32 ビット符号なし整数。<br /><br /> 非 CLS 準拠|**UInteger**|**uint**|**unsigned int**<br /><br /> または<br /><br /> **unsigned long**|**UInt32**|  
||<xref:System.UInt64>|64 ビット符号なし整数。<br /><br /> 非 CLS 準拠|**ULong**|**ulong**|**unsigned \_\_int64**|**UInt64**|  
|浮動小数点数|<xref:System.Single>|単精度 \(32 ビット\) 浮動小数点数|**Single**|**float**|**float**|**float**|  
||<xref:System.Double>|倍精度 \(64 ビット\) 浮動小数点数|**Double \(倍精度浮動小数点型\)**|**double**|**double**|**double**|  
|論理|<xref:System.Boolean>|ブール値 \(true または false\)|**Boolean**|**bool**|**bool**|**bool**|  
|その他|<xref:System.Char>|Unicode \(16 ビット\) 文字|**Char**|**char**|**wchar\_t**|**char**|  
||<xref:System.Decimal>|十進数 \(128 ビット\) の値です。|**Decimal \(10 進数型\)**|**decimal**|**Decimal \(10 進数型\)**|**Decimal \(10 進数型\)**|  
||<xref:System.IntPtr>|基になるプラットフォームによってサイズが決まる符号付き整数 \(32 ビットのプラットフォームでは 32 ビット値、64 ビットのプラットフォームでは 64 ビット値\)|**IntPtr**<br /><br /> 非組み込み型|**IntPtr**<br /><br /> 非組み込み型|**IntPtr**<br /><br /> 非組み込み型|**IntPtr**|  
||<xref:System.UIntPtr>|基になるプラットフォームによってサイズが決まる符号なし整数 \(32 ビットのプラットフォームでは 32 ビット値、64 ビットのプラットフォームでは 64 ビット値\)<br /><br /> 非 CLS 準拠|**UIntPtr**<br /><br /> 非組み込み型|**UIntPtr**<br /><br /> 非組み込み型|**UIntPtr**<br /><br /> 非組み込み型|**UIntPtr**|  
|クラス オブジェクト|<xref:System.Object>|オブジェクト階層構造のルート|**Object**|**object**|**Object\***|**Object**|  
||<xref:System.String>|Unicode 文字の不変固定長文字列|**String**|**string**|**String\***|**String**|  
  
 基本データ型に加えて、<xref:System> 名前空間には、例外を処理するクラスから、核となるランタイム概念 \(アプリケーション ドメインやガベージ コレクターなど\) を扱うクラスまで、100 以上のクラスが含まれます。  <xref:System> 名前空間には、2 次レベルの名前空間も数多く含まれています。  
  
 名前空間の詳細については、「[.NET Framework クラス ライブラリ](http://go.microsoft.com/fwlink/?LinkID=227195)」を参照してください。  参照ドキュメントには、各名前空間の簡単な概要と、各型とそのメンバーについての説明が記載されています。  
  
## 参照  
 [共通型システム](../../docs/standard/base-types/common-type-system.md)   
 [.NET Framework クラス ライブラリ](http://go.microsoft.com/fwlink/?LinkID=227195)   
 [概要](../../docs/framework/get-started/overview.md)