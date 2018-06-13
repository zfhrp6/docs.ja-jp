---
title: DateTime XAML 構文
ms.date: 03/30/2017
helpviewer_keywords:
- DateTime XAML syntax [WPF], strings for
- DateTime XAML syntax [WPF], where used
- short date format [WPF], DateTime
- DateTime XAML syntax [WPF]
- DateTime XAML text [WPF]
- DateTime XAML syntax [WPF], format strings for
ms.assetid: 5901710a-609b-40c8-9d65-f0016cd9090b
ms.openlocfilehash: 286117cc0cce9fb54ea2c372360b13865fba77ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540564"
---
# <a name="datetime-xaml-syntax"></a>DateTime XAML 構文
などのいくつかのコントロール<xref:System.Windows.Controls.Calendar>と<xref:System.Windows.Controls.DatePicker>、使用できるプロパティがあります、<xref:System.DateTime>型です。 これらのコントロールに対する日付または時刻の初期値は、分離コードで実行時に指定するのが一般的です。ただし、日付または時刻の初期値を XAML で指定することもできます。 WPF XAML パーサーの解析を処理する<xref:System.DateTime>組み込み XAML テキスト構文を使用して値をします。 このトピックの詳細を記述する、 <xref:System.DateTime> XAML テキスト構文です。  
  
  
<a name="where_datetime_xaml_syntax_is_used"></a>   
## <a name="when-to-use-datetime-xaml-syntax"></a>DateTime XAML 構文が使用される状況  
 日付は必ずしも XAML で設定する必要はありません。また、XAML で設定することが適切とは言えない場合もあります。 たとえば、使用する、<xref:System.DateTime.Now%2A?displayProperty=nameWithType>実行時、またはにする日付を初期化するためにプロパティが、分離コードでユーザー入力に基づいて予定表のすべての日付の調整を行う可能性があります。 ただし、シナリオにハードコードされた日付にすることがありますが、<xref:System.Windows.Controls.Calendar>と<xref:System.Windows.Controls.DatePicker>コントロール テンプレートにします。 <xref:System.DateTime> XAML 構文は、これらのシナリオのために使用する必要があります。  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a>DateTime XAML 構文はネイティブの動作  
 <xref:System.DateTime> CLR の基底クラス ライブラリで定義されているクラスです。 ため基底クラス ライブラリは、CLR の残りの部分に関連付ける方法、そのことはできませんを適用する<xref:System.ComponentModel.TypeConverterAttribute>クラスを XAML から文字列を処理および変換を実行する型コンバーターを使用して<xref:System.DateTime>ランタイム オブジェクト モデルでします。 変換動作を提供する `DateTimeConverter` クラスは存在しません。このトピックで説明する変換動作は、WPF XAML パーサーのネイティブな動作です。  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>   
## <a name="format-strings-for-datetime-xaml-syntax"></a>DateTime XAML 構文の書式指定文字列  
 形式を指定することができます、<xref:System.DateTime>書式指定文字列。 書式指定文字列は、値を作成するときに使用できるテキスト構文を形式化します。 <xref:System.DateTime> 値は既存の WPF コントロールの日付の構成要素が一般にのみ使用して<xref:System.DateTime>および時間コンポーネントではありません。  
  
 指定する場合、 <xref:System.DateTime> XAML では、置き換えて使用できます、書式指定文字列のいずれか。  
  
 また、このトピックで特に示されていない形式および書式指定文字列も使用できます。 技術的には、いずれかの XAML<xref:System.DateTime>が指定され、WPF XAML パーサーによって解析される値への内部呼び出しを使用して<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>、したがってで受け入れられる任意の文字列を使用する<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>XAML 入力します。 詳細については、「<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>」を参照してください。  
  
> [!IMPORTANT]
>  DateTime は、XAML 構文は常に使用`en-us`として、<xref:System.Globalization.CultureInfo>ネイティブ変換用。 これを受けない<xref:System.Windows.FrameworkElement.Language%2A>値または`xml:lang`XAML 属性のレベルの型変換がそのコンテキストを使用せずに動作するために、xaml で値します。 日や月を表示する順序などにはカルチャによる違いがあるため、ここで示した書式指定文字列は補完しないでください。 ここで示した書式指定文字列は、その他のカルチャ設定に関係なく、XAML を解析する場合に適しています。  
  
 以下のセクションでは、共通のいくつかについて説明<xref:System.DateTime>書式指定文字列。  
  
### <a name="short-date-pattern-d"></a>短い形式の日付パターン ("d")  
 次の短い日付形式を示しています、 <xref:System.DateTime> XAML で。  
  
 `M/d/YYYY`  
  
 これは、WPF コントロールでの一般的な使用法で、必要なすべての情報を指定するための最も簡単な形式です。タイム ゾーン オフセットと時刻要素を誤って指定した場合でも影響を受けないため、他の形式ではなく、この形式の使用をお勧めします。  
  
 たとえば、2010 年 6 月 1 日を指定するには、次の文字列を使用します。  
  
 `3/1/2010`  
  
 詳細については、「<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>」を参照してください。  
  
### <a name="sortable-datetime-pattern-s"></a>並べ替えできる DateTime のパターン ("s")  
 次の表示、並べ替え可能な<xref:System.DateTime>XAML 内のパターン。  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 たとえば、2010 年 6 月 1 日を指定するには、次の文字列を使用します (時刻要素はすべて 0 として入力されます)。  
  
 `2010-06-01T000:00:00`  
  
### <a name="rfc1123-pattern-r"></a>RFC1123 パターン ("r")  
 RFC1123 パターンの利点は、カルチャに依存しないために、RFC1123 パターンが使用されている他の日付ジェネレーターから入力された文字列を使用できることです。 次に示します RFC1123 <xref:System.DateTime> XAML 内のパターン。  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 たとえば、2010 年 6 月 1 日を指定するには、次の文字列を使用します (時刻要素はすべて 0 として入力されます)。  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### <a name="other-formats-and-patterns"></a>その他の形式とパターン  
 以前は、ように、 <xref:System.DateTime> XAML では、許容される任意の文字列として指定できますの入力として<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>です。 形式化されたその他の形式が含まれます (たとえば<xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>)、および特定として形式化されていない形式<xref:System.Globalization.DateTimeFormatInfo>フォーム。 たとえば、フォーム`YYYY/mm/dd`が許容されるの入力として<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>です。 このトピックでは、使用可能な形式の一部を説明します。標準的な使用手順としては、短い形式の日付パターンをお勧めします。  
  
## <a name="see-also"></a>関連項目  
 [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
