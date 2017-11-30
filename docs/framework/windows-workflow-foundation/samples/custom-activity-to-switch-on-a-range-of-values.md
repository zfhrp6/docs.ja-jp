---
title: "値の範囲で切り替えを行うカスタム アクティビティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 441e0a17-421f-430c-ba97-59e4cc6c88e3
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ff6a55157e886b54d631d1ca5d2598785de7608d
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2017
---
# <a name="custom-activity-to-switch-on-a-range-of-values"></a>値の範囲で切り替えを行うカスタム アクティビティ
このサンプルでは、<xref:System.Activities.Statements.Switch%601> の使用を拡張するカスタム アクティビティを作成する方法を示します。 従来の <xref:System.Activities.Statements.Switch%601> ステートメントでは、単一の値に基づく切り替えが可能です。 しかし、ビジネス上のシナリオでは、値の範囲に基づいて切り替えを行う必要があるアクティビティもあります。 たとえば、切り替えの基準となる値が 1 ～ 5 の場合はあるアクションを実行し、6 ～ 10 の場合は別のアクションを実行し、それ以外の値の場合は既定のアクションを実行するようなアクティビティもあります。 このカスタム アクティビティを使用すると、そのようなシナリオが可能になります。  
  
## <a name="the-switchrange-activity"></a>SwitchRange アクティビティ  
 `SwitchRange` アクティビティは、式の結果の値がいずれかの `Cases` の範囲内に含まれる場合に子アクティビティをスケジュールします。  
  
 値の範囲に基づいて切り替えを行うカスタム アクティビティのコード例を次に示します。  
  
```csharp  
public sealed class SwitchRange<T> : NativeActivity where T : IComparable  
{  
   [RequiredArgument]  
   [DefaultValue(null)]  
   public InArgument<T> Expression { get; set; }  
  
   public IList<CaseRange<T>> Cases  
  
   [DefaultValue(null)]  
   public Activity Default { get; set; }}  
}  
```  
  
|プロパティ|説明|  
|-|-|  
|式|評価されて Cases リストの範囲と比較される式です。 式の結果は T 型です。|  
|Cases|各ケースは、範囲 (From および To) とアクティビティ (Body) で構成されます。 式が評価されて範囲と比較され、 式の結果がいずれかのケースの範囲内の値になると、対応するアクティビティが実行されます。|  
|既定値|一致するケースがない場合に実行されるアクティビティです。 `null` に設定されている場合、アクションは実行されません。|  
  
## <a name="caserange-class"></a>CaseRange クラス  
 `CaseRange` クラスは、`SwitchRange` アクティビティ内の範囲を表します。 `CaseRange` の各インスタンスには、範囲 (`From` および `To`) と、`Body` の式の評価結果が範囲内の値になった場合にスケジュールされる `SwitchRange` アクティビティが含まれます。  
  
 `CaseRange` クラスの定義のコード例を次に示します。  
  
```  
public class CaseRange<T> where T : IComparable  
{  
    public T From { get; set; }  
  
    public T To { get; set; }  
  
    public Activity Action { get; set; }  
}  
```  
  
> [!NOTE]
>  このサンプルで定義されている `SwitchRange` クラスと `CaseRange` クラスはどちらも、`IComparable` クラスと同様に、<xref:System.Activities.Statements.Switch%601> を実装する任意の型で実行できるジェネリック クラスです。  
  
## <a name="sample-usage"></a>サンプルの使用方法  
 `SwitchRange` アクティビティの使用方法を次のコード例に示します。  
  
```csharp  
Activity SwitchRange = new SwitchRange<int>  
{  
    Expression = new InArgument<int>(value),  
    Cases =   
    {  
        new CaseRange<int>                      
        {  
            From = 1,  
            To = 5,  
            Action = new WriteLine  
            {  
                Text = "Case 1-5 selected",  
            }  
        },  
        new CaseRange<int>  
        {  
            From = 6,  
            To = 10,  
            Action = new WriteLine  
            {  
                Text = "Case 6-10 selected",  
            }  
        }  
    },  
    Default = new WriteLine { Text = "Default Case selected" }  
};  
```  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、SwitchRange.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SwitchRange`