---
title: "ODBC スキーマ コレクション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: b8c31f4e8b1463c184c9a8ff1cf64808783f030d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="d87f1-102">ODBC スキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="d87f1-102">ODBC Schema Collections</span></span>
<span data-ttu-id="d87f1-103">ここでは、Microsoft SQL Server、Oracle、および Microsoft Jet 用の各 ODBC ドライバーでのスキーマ コレクションのサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d87f1-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="d87f1-104">Microsoft SQL Server ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="d87f1-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="d87f1-105">Microsoft SQL Server ODBC Driver は、共通のスキーマ コレクションに加えて次の特定のスキーマ コレクションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="d87f1-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="d87f1-106">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="d87f1-106">Tables</span></span>  
  
-   <span data-ttu-id="d87f1-107">Indexes</span><span class="sxs-lookup"><span data-stu-id="d87f1-107">Indexes</span></span>  
  
-   <span data-ttu-id="d87f1-108">列</span><span class="sxs-lookup"><span data-stu-id="d87f1-108">Columns</span></span>  
  
-   <span data-ttu-id="d87f1-109">手順</span><span class="sxs-lookup"><span data-stu-id="d87f1-109">Procedures</span></span>  
  
-   <span data-ttu-id="d87f1-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="d87f1-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="d87f1-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="d87f1-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="d87f1-112">ビュー</span><span class="sxs-lookup"><span data-stu-id="d87f1-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="d87f1-113">Tables と Views</span><span class="sxs-lookup"><span data-stu-id="d87f1-113">Tables and Views</span></span>  
  
|<span data-ttu-id="d87f1-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d87f1-114">ColumnName</span></span>|<span data-ttu-id="d87f1-115">DataType</span><span class="sxs-lookup"><span data-stu-id="d87f1-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d87f1-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="d87f1-116">TABLE_CAT</span></span>|<span data-ttu-id="d87f1-117">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-117">String</span></span>|  
|<span data-ttu-id="d87f1-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="d87f1-118">TABLE_SCHEM</span></span>|<span data-ttu-id="d87f1-119">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-119">String</span></span>|  
|<span data-ttu-id="d87f1-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-120">TABLE_NAME</span></span>|<span data-ttu-id="d87f1-121">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-121">String</span></span>|  
|<span data-ttu-id="d87f1-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-122">TABLE_TYPE</span></span>|<span data-ttu-id="d87f1-123">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-123">String</span></span>|  
|<span data-ttu-id="d87f1-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="d87f1-124">REMARKS</span></span>|<span data-ttu-id="d87f1-125">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="d87f1-126">Indexes</span><span class="sxs-lookup"><span data-stu-id="d87f1-126">Indexes</span></span>  
  
|<span data-ttu-id="d87f1-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d87f1-127">ColumnName</span></span>|<span data-ttu-id="d87f1-128">DataType</span><span class="sxs-lookup"><span data-stu-id="d87f1-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d87f1-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="d87f1-129">TABLE_CAT</span></span>|<span data-ttu-id="d87f1-130">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-130">String</span></span>|  
|<span data-ttu-id="d87f1-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="d87f1-131">TABLE_SCHEM</span></span>|<span data-ttu-id="d87f1-132">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-132">String</span></span>|  
|<span data-ttu-id="d87f1-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-133">TABLE_NAME</span></span>|<span data-ttu-id="d87f1-134">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-134">String</span></span>|  
|<span data-ttu-id="d87f1-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="d87f1-135">NON_UNIQUE</span></span>|<span data-ttu-id="d87f1-136">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-136">Int16</span></span>|  
|<span data-ttu-id="d87f1-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="d87f1-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="d87f1-138">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-138">String</span></span>|  
|<span data-ttu-id="d87f1-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-139">INDEX_NAME</span></span>|<span data-ttu-id="d87f1-140">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-140">String</span></span>|  
|<span data-ttu-id="d87f1-141">TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-141">TYPE</span></span>|<span data-ttu-id="d87f1-142">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-142">Int16</span></span>|  
|<span data-ttu-id="d87f1-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d87f1-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="d87f1-144">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-144">Int16</span></span>|  
|<span data-ttu-id="d87f1-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-145">COLUMN_NAME</span></span>|<span data-ttu-id="d87f1-146">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-146">String</span></span>|  
|<span data-ttu-id="d87f1-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="d87f1-147">ASC_OR_DESC</span></span>|<span data-ttu-id="d87f1-148">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-148">String</span></span>|  
|<span data-ttu-id="d87f1-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="d87f1-149">CARDINATLITY</span></span>|<span data-ttu-id="d87f1-150">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-150">Int32</span></span>|  
|<span data-ttu-id="d87f1-151">PAGES</span><span class="sxs-lookup"><span data-stu-id="d87f1-151">PAGES</span></span>|<span data-ttu-id="d87f1-152">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-152">Int32</span></span>|  
|<span data-ttu-id="d87f1-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="d87f1-153">FILTER_CONDITION</span></span>|<span data-ttu-id="d87f1-154">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-154">String</span></span>|  
|<span data-ttu-id="d87f1-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d87f1-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="d87f1-156">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-156">String</span></span>|  
|<span data-ttu-id="d87f1-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="d87f1-158">Byte</span><span class="sxs-lookup"><span data-stu-id="d87f1-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="d87f1-159">列</span><span class="sxs-lookup"><span data-stu-id="d87f1-159">Columns</span></span>  
  
|<span data-ttu-id="d87f1-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d87f1-160">ColumnName</span></span>|<span data-ttu-id="d87f1-161">DataType</span><span class="sxs-lookup"><span data-stu-id="d87f1-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d87f1-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="d87f1-162">TABLE_CAT</span></span>|<span data-ttu-id="d87f1-163">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-163">String</span></span>|  
|<span data-ttu-id="d87f1-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="d87f1-164">TABLE_SCHEM</span></span>|<span data-ttu-id="d87f1-165">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-165">String</span></span>|  
|<span data-ttu-id="d87f1-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-166">TABLE_NAME</span></span>|<span data-ttu-id="d87f1-167">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-167">String</span></span>|  
|<span data-ttu-id="d87f1-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-168">COLUMN_NAME</span></span>|<span data-ttu-id="d87f1-169">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-169">String</span></span>|  
|<span data-ttu-id="d87f1-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-170">DATA_TYPE</span></span>|<span data-ttu-id="d87f1-171">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-171">Int16</span></span>|  
|<span data-ttu-id="d87f1-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-172">TYPE_NAME</span></span>|<span data-ttu-id="d87f1-173">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-173">String</span></span>|  
|<span data-ttu-id="d87f1-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="d87f1-174">COLUMN_SIZE</span></span>|<span data-ttu-id="d87f1-175">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-175">Int32</span></span>|  
|<span data-ttu-id="d87f1-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d87f1-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="d87f1-177">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-177">Int32</span></span>|  
|<span data-ttu-id="d87f1-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="d87f1-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="d87f1-179">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-179">Int16</span></span>|  
|<span data-ttu-id="d87f1-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="d87f1-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="d87f1-181">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-181">Int16</span></span>|  
|<span data-ttu-id="d87f1-182">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d87f1-182">NULLABLE</span></span>|<span data-ttu-id="d87f1-183">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-183">Int16</span></span>|  
|<span data-ttu-id="d87f1-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="d87f1-184">REMARKS</span></span>|<span data-ttu-id="d87f1-185">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-185">String</span></span>|  
|<span data-ttu-id="d87f1-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="d87f1-186">COLUMN_DEF</span></span>|<span data-ttu-id="d87f1-187">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-187">String</span></span>|  
|<span data-ttu-id="d87f1-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="d87f1-189">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-189">Int16</span></span>|  
|<span data-ttu-id="d87f1-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="d87f1-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="d87f1-191">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-191">Int16</span></span>|  
|<span data-ttu-id="d87f1-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d87f1-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="d87f1-193">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-193">Int32</span></span>|  
|<span data-ttu-id="d87f1-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d87f1-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="d87f1-195">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-195">Int32</span></span>|  
|<span data-ttu-id="d87f1-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d87f1-196">IS_NULLABLE</span></span>|<span data-ttu-id="d87f1-197">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-197">String</span></span>|  
|<span data-ttu-id="d87f1-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d87f1-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="d87f1-199">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-199">String</span></span>|  
|<span data-ttu-id="d87f1-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d87f1-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="d87f1-201">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-201">String</span></span>|  
|<span data-ttu-id="d87f1-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="d87f1-203">Byte</span><span class="sxs-lookup"><span data-stu-id="d87f1-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="d87f1-204">手順</span><span class="sxs-lookup"><span data-stu-id="d87f1-204">Procedures</span></span>  
  
|<span data-ttu-id="d87f1-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d87f1-205">ColumnName</span></span>|<span data-ttu-id="d87f1-206">DataType</span><span class="sxs-lookup"><span data-stu-id="d87f1-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d87f1-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="d87f1-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="d87f1-208">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-208">String</span></span>|  
|<span data-ttu-id="d87f1-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="d87f1-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="d87f1-210">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-210">String</span></span>|  
|<span data-ttu-id="d87f1-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="d87f1-212">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-212">String</span></span>|  
|<span data-ttu-id="d87f1-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="d87f1-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="d87f1-214">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-214">Int32</span></span>|  
|<span data-ttu-id="d87f1-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="d87f1-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="d87f1-216">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-216">Int32</span></span>|  
|<span data-ttu-id="d87f1-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="d87f1-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="d87f1-218">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-218">Int32</span></span>|  
|<span data-ttu-id="d87f1-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="d87f1-219">REMARKS</span></span>|<span data-ttu-id="d87f1-220">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-220">String</span></span>|  
|<span data-ttu-id="d87f1-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="d87f1-222">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="d87f1-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="d87f1-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="d87f1-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d87f1-224">ColumnName</span></span>|<span data-ttu-id="d87f1-225">DataType</span><span class="sxs-lookup"><span data-stu-id="d87f1-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d87f1-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="d87f1-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="d87f1-227">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-227">String</span></span>|  
|<span data-ttu-id="d87f1-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="d87f1-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="d87f1-229">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-229">String</span></span>|  
|<span data-ttu-id="d87f1-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="d87f1-231">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-231">String</span></span>|  
|<span data-ttu-id="d87f1-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-232">COLUMN_NAME</span></span>|<span data-ttu-id="d87f1-233">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-233">String</span></span>|  
|<span data-ttu-id="d87f1-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-234">COLUMN_TYPE</span></span>|<span data-ttu-id="d87f1-235">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-235">Int16</span></span>|  
|<span data-ttu-id="d87f1-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-236">DATA_TYPE</span></span>|<span data-ttu-id="d87f1-237">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-237">Int16</span></span>|  
|<span data-ttu-id="d87f1-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-238">TYPE_NAME</span></span>|<span data-ttu-id="d87f1-239">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-239">String</span></span>|  
|<span data-ttu-id="d87f1-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="d87f1-240">COLUMN_SIZE</span></span>|<span data-ttu-id="d87f1-241">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-241">Int32</span></span>|  
|<span data-ttu-id="d87f1-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d87f1-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="d87f1-243">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-243">Int32</span></span>|  
|<span data-ttu-id="d87f1-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="d87f1-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="d87f1-245">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-245">Int16</span></span>|  
|<span data-ttu-id="d87f1-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="d87f1-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="d87f1-247">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-247">Int16</span></span>|  
|<span data-ttu-id="d87f1-248">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d87f1-248">NULLABLE</span></span>|<span data-ttu-id="d87f1-249">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-249">Int16</span></span>|  
|<span data-ttu-id="d87f1-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="d87f1-250">REMARKS</span></span>|<span data-ttu-id="d87f1-251">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-251">String</span></span>|  
|<span data-ttu-id="d87f1-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="d87f1-252">COLUMN_DEF</span></span>|<span data-ttu-id="d87f1-253">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-253">String</span></span>|  
|<span data-ttu-id="d87f1-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="d87f1-255">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-255">Int16</span></span>|  
|<span data-ttu-id="d87f1-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="d87f1-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="d87f1-257">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-257">Int16</span></span>|  
|<span data-ttu-id="d87f1-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d87f1-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="d87f1-259">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-259">Int32</span></span>|  
|<span data-ttu-id="d87f1-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d87f1-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="d87f1-261">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-261">Int32</span></span>|  
|<span data-ttu-id="d87f1-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d87f1-262">IS_NULLABLE</span></span>|<span data-ttu-id="d87f1-263">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-263">String</span></span>|  
|<span data-ttu-id="d87f1-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d87f1-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="d87f1-265">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-265">String</span></span>|  
|<span data-ttu-id="d87f1-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d87f1-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="d87f1-267">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-267">String</span></span>|  
|<span data-ttu-id="d87f1-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="d87f1-269">Byte</span><span class="sxs-lookup"><span data-stu-id="d87f1-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="d87f1-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="d87f1-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="d87f1-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d87f1-271">ColumnName</span></span>|<span data-ttu-id="d87f1-272">DataType</span><span class="sxs-lookup"><span data-stu-id="d87f1-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d87f1-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="d87f1-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="d87f1-274">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-274">String</span></span>|  
|<span data-ttu-id="d87f1-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="d87f1-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="d87f1-276">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-276">String</span></span>|  
|<span data-ttu-id="d87f1-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="d87f1-278">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-278">String</span></span>|  
|<span data-ttu-id="d87f1-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-279">COLUMN_NAME</span></span>|<span data-ttu-id="d87f1-280">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-280">String</span></span>|  
|<span data-ttu-id="d87f1-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-281">COLUMN_TYPE</span></span>|<span data-ttu-id="d87f1-282">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-282">Int16</span></span>|  
|<span data-ttu-id="d87f1-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-283">DATA_TYPE</span></span>|<span data-ttu-id="d87f1-284">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-284">Int16</span></span>|  
|<span data-ttu-id="d87f1-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-285">TYPE_NAME</span></span>|<span data-ttu-id="d87f1-286">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-286">String</span></span>|  
|<span data-ttu-id="d87f1-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="d87f1-287">COLUMN_SIZE</span></span>|<span data-ttu-id="d87f1-288">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-288">Int32</span></span>|  
|<span data-ttu-id="d87f1-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d87f1-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="d87f1-290">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-290">Int32</span></span>|  
|<span data-ttu-id="d87f1-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="d87f1-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="d87f1-292">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-292">Int16</span></span>|  
|<span data-ttu-id="d87f1-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="d87f1-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="d87f1-294">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-294">Int16</span></span>|  
|<span data-ttu-id="d87f1-295">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d87f1-295">NULLABLE</span></span>|<span data-ttu-id="d87f1-296">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-296">Int16</span></span>|  
|<span data-ttu-id="d87f1-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="d87f1-297">REMARKS</span></span>|<span data-ttu-id="d87f1-298">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-298">String</span></span>|  
|<span data-ttu-id="d87f1-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="d87f1-299">COLUMN_DEF</span></span>|<span data-ttu-id="d87f1-300">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-300">String</span></span>|  
|<span data-ttu-id="d87f1-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="d87f1-302">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-302">Int16</span></span>|  
|<span data-ttu-id="d87f1-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="d87f1-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="d87f1-304">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-304">Int16</span></span>|  
|<span data-ttu-id="d87f1-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d87f1-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="d87f1-306">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-306">Int32</span></span>|  
|<span data-ttu-id="d87f1-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d87f1-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="d87f1-308">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-308">Int32</span></span>|  
|<span data-ttu-id="d87f1-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d87f1-309">IS_NULLABLE</span></span>|<span data-ttu-id="d87f1-310">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-310">String</span></span>|  
|<span data-ttu-id="d87f1-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d87f1-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="d87f1-312">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-312">String</span></span>|  
|<span data-ttu-id="d87f1-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d87f1-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="d87f1-314">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-314">String</span></span>|  
|<span data-ttu-id="d87f1-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="d87f1-316">Byte</span><span class="sxs-lookup"><span data-stu-id="d87f1-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="d87f1-317">Microsoft Oracle ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="d87f1-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="d87f1-318">Microsoft SQL Server Oracle ODBC Driver は、共通のスキーマ コレクションに加えて次の特定のスキーマ コレクションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="d87f1-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="d87f1-319">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="d87f1-319">Tables</span></span>  
  
-   <span data-ttu-id="d87f1-320">列</span><span class="sxs-lookup"><span data-stu-id="d87f1-320">Columns</span></span>  
  
-   <span data-ttu-id="d87f1-321">手順</span><span class="sxs-lookup"><span data-stu-id="d87f1-321">Procedures</span></span>  
  
-   <span data-ttu-id="d87f1-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="d87f1-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="d87f1-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="d87f1-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="d87f1-324">ビュー</span><span class="sxs-lookup"><span data-stu-id="d87f1-324">Views</span></span>  
  
-   <span data-ttu-id="d87f1-325">Indexes</span><span class="sxs-lookup"><span data-stu-id="d87f1-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="d87f1-326">Tables と Views</span><span class="sxs-lookup"><span data-stu-id="d87f1-326">Tables and Views</span></span>  
  
|<span data-ttu-id="d87f1-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d87f1-327">ColumnName</span></span>|<span data-ttu-id="d87f1-328">DataType</span><span class="sxs-lookup"><span data-stu-id="d87f1-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d87f1-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="d87f1-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="d87f1-330">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-330">String</span></span>|  
|<span data-ttu-id="d87f1-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="d87f1-331">TABLE_OWNER</span></span>|<span data-ttu-id="d87f1-332">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-332">String</span></span>|  
|<span data-ttu-id="d87f1-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-333">TABLE_NAME</span></span>|<span data-ttu-id="d87f1-334">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-334">String</span></span>|  
|<span data-ttu-id="d87f1-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-335">TABLE_TYPE</span></span>|<span data-ttu-id="d87f1-336">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-336">String</span></span>|  
|<span data-ttu-id="d87f1-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="d87f1-337">REMARKS</span></span>|<span data-ttu-id="d87f1-338">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="d87f1-339">列</span><span class="sxs-lookup"><span data-stu-id="d87f1-339">Columns</span></span>  
  
|<span data-ttu-id="d87f1-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d87f1-340">ColumnName</span></span>|<span data-ttu-id="d87f1-341">DataType</span><span class="sxs-lookup"><span data-stu-id="d87f1-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d87f1-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="d87f1-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="d87f1-343">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-343">String</span></span>|  
|<span data-ttu-id="d87f1-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="d87f1-344">TABLE_OWNER</span></span>|<span data-ttu-id="d87f1-345">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-345">String</span></span>|  
|<span data-ttu-id="d87f1-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-346">TABLE_NAME</span></span>|<span data-ttu-id="d87f1-347">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-347">String</span></span>|  
|<span data-ttu-id="d87f1-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-348">COLUMN_NAME</span></span>|<span data-ttu-id="d87f1-349">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-349">String</span></span>|  
|<span data-ttu-id="d87f1-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-350">DATA_TYPE</span></span>|<span data-ttu-id="d87f1-351">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-351">Int16</span></span>|  
|<span data-ttu-id="d87f1-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-352">TYPE_NAME</span></span>|<span data-ttu-id="d87f1-353">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-353">String</span></span>|  
|<span data-ttu-id="d87f1-354">PRECISION</span><span class="sxs-lookup"><span data-stu-id="d87f1-354">PRECISION</span></span>|<span data-ttu-id="d87f1-355">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-355">Int32</span></span>|  
|<span data-ttu-id="d87f1-356">LENGTH</span><span class="sxs-lookup"><span data-stu-id="d87f1-356">LENGTH</span></span>|<span data-ttu-id="d87f1-357">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-357">Int32</span></span>|  
|<span data-ttu-id="d87f1-358">SCALE</span><span class="sxs-lookup"><span data-stu-id="d87f1-358">SCALE</span></span>|<span data-ttu-id="d87f1-359">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-359">Int16</span></span>|  
|<span data-ttu-id="d87f1-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="d87f1-360">RADIX</span></span>|<span data-ttu-id="d87f1-361">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-361">Int16</span></span>|  
|<span data-ttu-id="d87f1-362">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d87f1-362">NULLABLE</span></span>|<span data-ttu-id="d87f1-363">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-363">Int16</span></span>|  
|<span data-ttu-id="d87f1-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="d87f1-364">REMARKS</span></span>|<span data-ttu-id="d87f1-365">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-365">String</span></span>|  
|<span data-ttu-id="d87f1-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d87f1-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="d87f1-367">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="d87f1-368">手順</span><span class="sxs-lookup"><span data-stu-id="d87f1-368">Procedures</span></span>  
  
|<span data-ttu-id="d87f1-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d87f1-369">ColumnName</span></span>|<span data-ttu-id="d87f1-370">DataType</span><span class="sxs-lookup"><span data-stu-id="d87f1-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d87f1-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="d87f1-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="d87f1-372">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-372">String</span></span>|  
|<span data-ttu-id="d87f1-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="d87f1-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="d87f1-374">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-374">String</span></span>|  
|<span data-ttu-id="d87f1-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="d87f1-376">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-376">String</span></span>|  
|<span data-ttu-id="d87f1-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="d87f1-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="d87f1-378">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-378">Int16</span></span>|  
|<span data-ttu-id="d87f1-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="d87f1-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="d87f1-380">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-380">Int16</span></span>|  
|<span data-ttu-id="d87f1-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="d87f1-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="d87f1-382">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-382">Int16</span></span>|  
|<span data-ttu-id="d87f1-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="d87f1-383">REMARKS</span></span>|<span data-ttu-id="d87f1-384">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-384">String</span></span>|  
|<span data-ttu-id="d87f1-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="d87f1-386">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="d87f1-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="d87f1-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="d87f1-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d87f1-388">ColumnName</span></span>|<span data-ttu-id="d87f1-389">DataType</span><span class="sxs-lookup"><span data-stu-id="d87f1-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d87f1-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="d87f1-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="d87f1-391">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-391">String</span></span>|  
|<span data-ttu-id="d87f1-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="d87f1-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="d87f1-393">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-393">String</span></span>|  
|<span data-ttu-id="d87f1-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="d87f1-395">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-395">String</span></span>|  
|<span data-ttu-id="d87f1-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-396">COLUMN_NAME</span></span>|<span data-ttu-id="d87f1-397">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-397">String</span></span>|  
|<span data-ttu-id="d87f1-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-398">COLUMN_TYPE</span></span>|<span data-ttu-id="d87f1-399">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-399">Int16</span></span>|  
|<span data-ttu-id="d87f1-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-400">DATA_TYPE</span></span>|<span data-ttu-id="d87f1-401">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-401">Int16</span></span>|  
|<span data-ttu-id="d87f1-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-402">TYPE_NAME</span></span>|<span data-ttu-id="d87f1-403">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-403">String</span></span>|  
|<span data-ttu-id="d87f1-404">PRECISION</span><span class="sxs-lookup"><span data-stu-id="d87f1-404">PRECISION</span></span>|<span data-ttu-id="d87f1-405">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-405">Int32</span></span>|  
|<span data-ttu-id="d87f1-406">LENGTH</span><span class="sxs-lookup"><span data-stu-id="d87f1-406">LENGTH</span></span>|<span data-ttu-id="d87f1-407">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-407">Int32</span></span>|  
|<span data-ttu-id="d87f1-408">SCALE</span><span class="sxs-lookup"><span data-stu-id="d87f1-408">SCALE</span></span>|<span data-ttu-id="d87f1-409">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-409">Int16</span></span>|  
|<span data-ttu-id="d87f1-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="d87f1-410">RADIX</span></span>|<span data-ttu-id="d87f1-411">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-411">Int16</span></span>|  
|<span data-ttu-id="d87f1-412">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d87f1-412">NULLABLE</span></span>|<span data-ttu-id="d87f1-413">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-413">Int16</span></span>|  
|<span data-ttu-id="d87f1-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="d87f1-414">REMARKS</span></span>|<span data-ttu-id="d87f1-415">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-415">String</span></span>|  
|<span data-ttu-id="d87f1-416">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="d87f1-416">OVERLOAD</span></span>|<span data-ttu-id="d87f1-417">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-417">Int32</span></span>|  
|<span data-ttu-id="d87f1-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d87f1-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="d87f1-419">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="d87f1-420">Microsoft Jet ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="d87f1-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="d87f1-421">Microsoft Jet ODBC Driver は、共通のスキーマ コレクションに加えて次のスキーマ コレクションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="d87f1-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="d87f1-422">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="d87f1-422">Tables</span></span>  
  
-   <span data-ttu-id="d87f1-423">Indexes</span><span class="sxs-lookup"><span data-stu-id="d87f1-423">Indexes</span></span>  
  
-   <span data-ttu-id="d87f1-424">列</span><span class="sxs-lookup"><span data-stu-id="d87f1-424">Columns</span></span>  
  
-   <span data-ttu-id="d87f1-425">手順</span><span class="sxs-lookup"><span data-stu-id="d87f1-425">Procedures</span></span>  
  
-   <span data-ttu-id="d87f1-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="d87f1-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="d87f1-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="d87f1-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="d87f1-428">ビュー</span><span class="sxs-lookup"><span data-stu-id="d87f1-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="d87f1-429">Tables と Views</span><span class="sxs-lookup"><span data-stu-id="d87f1-429">Tables and Views</span></span>  
  
|<span data-ttu-id="d87f1-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d87f1-430">ColumnName</span></span>|<span data-ttu-id="d87f1-431">DataType</span><span class="sxs-lookup"><span data-stu-id="d87f1-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d87f1-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="d87f1-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="d87f1-433">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-433">String</span></span>|  
|<span data-ttu-id="d87f1-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="d87f1-434">TABLE_OWNER</span></span>|<span data-ttu-id="d87f1-435">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-435">String</span></span>|  
|<span data-ttu-id="d87f1-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-436">TABLE_NAME</span></span>|<span data-ttu-id="d87f1-437">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-437">String</span></span>|  
|<span data-ttu-id="d87f1-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-438">TABLE_TYPE</span></span>|<span data-ttu-id="d87f1-439">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-439">String</span></span>|  
|<span data-ttu-id="d87f1-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="d87f1-440">REMARKS</span></span>|<span data-ttu-id="d87f1-441">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="d87f1-442">列</span><span class="sxs-lookup"><span data-stu-id="d87f1-442">Columns</span></span>  
  
|<span data-ttu-id="d87f1-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d87f1-443">ColumnName</span></span>|<span data-ttu-id="d87f1-444">DataType</span><span class="sxs-lookup"><span data-stu-id="d87f1-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d87f1-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="d87f1-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="d87f1-446">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-446">String</span></span>|  
|<span data-ttu-id="d87f1-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="d87f1-447">TABLE_OWNER</span></span>|<span data-ttu-id="d87f1-448">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-448">String</span></span>|  
|<span data-ttu-id="d87f1-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-449">TABLE_NAME</span></span>|<span data-ttu-id="d87f1-450">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-450">String</span></span>|  
|<span data-ttu-id="d87f1-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-451">COLUMN_NAME</span></span>|<span data-ttu-id="d87f1-452">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-452">String</span></span>|  
|<span data-ttu-id="d87f1-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-453">DATA_TYPE</span></span>|<span data-ttu-id="d87f1-454">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-454">Int16</span></span>|  
|<span data-ttu-id="d87f1-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-455">TYPE_NAME</span></span>|<span data-ttu-id="d87f1-456">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-456">String</span></span>|  
|<span data-ttu-id="d87f1-457">PRECISION</span><span class="sxs-lookup"><span data-stu-id="d87f1-457">PRECISION</span></span>|<span data-ttu-id="d87f1-458">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-458">Int32</span></span>|  
|<span data-ttu-id="d87f1-459">LENGTH</span><span class="sxs-lookup"><span data-stu-id="d87f1-459">LENGTH</span></span>|<span data-ttu-id="d87f1-460">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-460">Int32</span></span>|  
|<span data-ttu-id="d87f1-461">SCALE</span><span class="sxs-lookup"><span data-stu-id="d87f1-461">SCALE</span></span>|<span data-ttu-id="d87f1-462">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-462">Int16</span></span>|  
|<span data-ttu-id="d87f1-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="d87f1-463">RADIX</span></span>|<span data-ttu-id="d87f1-464">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-464">Int16</span></span>|  
|<span data-ttu-id="d87f1-465">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d87f1-465">NULLABLE</span></span>|<span data-ttu-id="d87f1-466">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-466">Int16</span></span>|  
|<span data-ttu-id="d87f1-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="d87f1-467">REMARKS</span></span>|<span data-ttu-id="d87f1-468">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-468">String</span></span>|  
|<span data-ttu-id="d87f1-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d87f1-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="d87f1-470">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="d87f1-471">手順</span><span class="sxs-lookup"><span data-stu-id="d87f1-471">Procedures</span></span>  
  
|<span data-ttu-id="d87f1-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d87f1-472">ColumnName</span></span>|<span data-ttu-id="d87f1-473">DataType</span><span class="sxs-lookup"><span data-stu-id="d87f1-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d87f1-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="d87f1-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="d87f1-475">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-475">String</span></span>|  
|<span data-ttu-id="d87f1-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="d87f1-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="d87f1-477">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-477">String</span></span>|  
|<span data-ttu-id="d87f1-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="d87f1-479">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-479">String</span></span>|  
|<span data-ttu-id="d87f1-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="d87f1-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="d87f1-481">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-481">Int16</span></span>|  
|<span data-ttu-id="d87f1-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="d87f1-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="d87f1-483">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-483">Int16</span></span>|  
|<span data-ttu-id="d87f1-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="d87f1-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="d87f1-485">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-485">Int16</span></span>|  
|<span data-ttu-id="d87f1-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="d87f1-486">REMARKS</span></span>|<span data-ttu-id="d87f1-487">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-487">String</span></span>|  
|<span data-ttu-id="d87f1-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="d87f1-489">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="d87f1-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="d87f1-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="d87f1-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d87f1-491">ColumnName</span></span>|<span data-ttu-id="d87f1-492">DataType</span><span class="sxs-lookup"><span data-stu-id="d87f1-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d87f1-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="d87f1-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="d87f1-494">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-494">String</span></span>|  
|<span data-ttu-id="d87f1-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="d87f1-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="d87f1-496">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-496">String</span></span>|  
|<span data-ttu-id="d87f1-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="d87f1-498">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-498">String</span></span>|  
|<span data-ttu-id="d87f1-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-499">COLUMN_NAME</span></span>|<span data-ttu-id="d87f1-500">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-500">String</span></span>|  
|<span data-ttu-id="d87f1-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-501">COLUMN_TYPE</span></span>|<span data-ttu-id="d87f1-502">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-502">Int16</span></span>|  
|<span data-ttu-id="d87f1-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-503">DATA_TYPE</span></span>|<span data-ttu-id="d87f1-504">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-504">Int16</span></span>|  
|<span data-ttu-id="d87f1-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-505">TYPE_NAME</span></span>|<span data-ttu-id="d87f1-506">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-506">String</span></span>|  
|<span data-ttu-id="d87f1-507">PRECISION</span><span class="sxs-lookup"><span data-stu-id="d87f1-507">PRECISION</span></span>|<span data-ttu-id="d87f1-508">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-508">Int32</span></span>|  
|<span data-ttu-id="d87f1-509">LENGTH</span><span class="sxs-lookup"><span data-stu-id="d87f1-509">LENGTH</span></span>|<span data-ttu-id="d87f1-510">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-510">Int32</span></span>|  
|<span data-ttu-id="d87f1-511">SCALE</span><span class="sxs-lookup"><span data-stu-id="d87f1-511">SCALE</span></span>|<span data-ttu-id="d87f1-512">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-512">Int16</span></span>|  
|<span data-ttu-id="d87f1-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="d87f1-513">RADIX</span></span>|<span data-ttu-id="d87f1-514">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-514">Int16</span></span>|  
|<span data-ttu-id="d87f1-515">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d87f1-515">NULLABLE</span></span>|<span data-ttu-id="d87f1-516">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-516">Int16</span></span>|  
|<span data-ttu-id="d87f1-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="d87f1-517">REMARKS</span></span>|<span data-ttu-id="d87f1-518">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-518">String</span></span>|  
|<span data-ttu-id="d87f1-519">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="d87f1-519">OVERLOAD</span></span>|<span data-ttu-id="d87f1-520">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-520">Int32</span></span>|  
|<span data-ttu-id="d87f1-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d87f1-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="d87f1-522">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="d87f1-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="d87f1-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="d87f1-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="d87f1-524">ColumnName</span></span>|<span data-ttu-id="d87f1-525">DataType</span><span class="sxs-lookup"><span data-stu-id="d87f1-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="d87f1-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="d87f1-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="d87f1-527">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-527">String</span></span>|  
|<span data-ttu-id="d87f1-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="d87f1-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="d87f1-529">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-529">String</span></span>|  
|<span data-ttu-id="d87f1-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="d87f1-531">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-531">String</span></span>|  
|<span data-ttu-id="d87f1-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-532">COLUMN_NAME</span></span>|<span data-ttu-id="d87f1-533">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-533">String</span></span>|  
|<span data-ttu-id="d87f1-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-534">COLUMN_TYPE</span></span>|<span data-ttu-id="d87f1-535">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-535">Int16</span></span>|  
|<span data-ttu-id="d87f1-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-536">DATA_TYPE</span></span>|<span data-ttu-id="d87f1-537">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-537">Int16</span></span>|  
|<span data-ttu-id="d87f1-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="d87f1-538">TYPE_NAME</span></span>|<span data-ttu-id="d87f1-539">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-539">String</span></span>|  
|<span data-ttu-id="d87f1-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="d87f1-540">COLUMN_SIZE</span></span>|<span data-ttu-id="d87f1-541">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-541">Int32</span></span>|  
|<span data-ttu-id="d87f1-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d87f1-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="d87f1-543">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-543">Int32</span></span>|  
|<span data-ttu-id="d87f1-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="d87f1-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="d87f1-545">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-545">Int16</span></span>|  
|<span data-ttu-id="d87f1-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="d87f1-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="d87f1-547">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-547">Int16</span></span>|  
|<span data-ttu-id="d87f1-548">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d87f1-548">NULLABLE</span></span>|<span data-ttu-id="d87f1-549">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-549">Int16</span></span>|  
|<span data-ttu-id="d87f1-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="d87f1-550">REMARKS</span></span>|<span data-ttu-id="d87f1-551">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-551">String</span></span>|  
|<span data-ttu-id="d87f1-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="d87f1-552">COLUMN_DEF</span></span>|<span data-ttu-id="d87f1-553">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-553">String</span></span>|  
|<span data-ttu-id="d87f1-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d87f1-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="d87f1-555">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-555">Int16</span></span>|  
|<span data-ttu-id="d87f1-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="d87f1-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="d87f1-557">Int16</span><span class="sxs-lookup"><span data-stu-id="d87f1-557">Int16</span></span>|  
|<span data-ttu-id="d87f1-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d87f1-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="d87f1-559">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-559">Int32</span></span>|  
|<span data-ttu-id="d87f1-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="d87f1-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="d87f1-561">Int32</span><span class="sxs-lookup"><span data-stu-id="d87f1-561">Int32</span></span>|  
|<span data-ttu-id="d87f1-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d87f1-562">IS_NULLABLE</span></span>|<span data-ttu-id="d87f1-563">String</span><span class="sxs-lookup"><span data-stu-id="d87f1-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d87f1-564">参照</span><span class="sxs-lookup"><span data-stu-id="d87f1-564">See Also</span></span>  
 [<span data-ttu-id="d87f1-565">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="d87f1-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
