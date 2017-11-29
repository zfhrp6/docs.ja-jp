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
ms.openlocfilehash: 889e84db39af1257d709ef049e18d4397ea700d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="f3b5c-102">ODBC スキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="f3b5c-102">ODBC Schema Collections</span></span>
<span data-ttu-id="f3b5c-103">ここでは、Microsoft SQL Server、Oracle、および Microsoft Jet 用の各 ODBC ドライバーでのスキーマ コレクションのサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f3b5c-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="f3b5c-104">Microsoft SQL Server ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="f3b5c-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="f3b5c-105">Microsoft SQL Server ODBC Driver は、共通のスキーマ コレクションに加えて次の特定のスキーマ コレクションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="f3b5c-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="f3b5c-106">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="f3b5c-106">Tables</span></span>  
  
-   <span data-ttu-id="f3b5c-107">Indexes</span><span class="sxs-lookup"><span data-stu-id="f3b5c-107">Indexes</span></span>  
  
-   <span data-ttu-id="f3b5c-108">列</span><span class="sxs-lookup"><span data-stu-id="f3b5c-108">Columns</span></span>  
  
-   <span data-ttu-id="f3b5c-109">手順</span><span class="sxs-lookup"><span data-stu-id="f3b5c-109">Procedures</span></span>  
  
-   <span data-ttu-id="f3b5c-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f3b5c-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="f3b5c-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f3b5c-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="f3b5c-112">ビュー</span><span class="sxs-lookup"><span data-stu-id="f3b5c-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="f3b5c-113">Tables と Views</span><span class="sxs-lookup"><span data-stu-id="f3b5c-113">Tables and Views</span></span>  
  
|<span data-ttu-id="f3b5c-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f3b5c-114">ColumnName</span></span>|<span data-ttu-id="f3b5c-115">DataType</span><span class="sxs-lookup"><span data-stu-id="f3b5c-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f3b5c-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="f3b5c-116">TABLE_CAT</span></span>|<span data-ttu-id="f3b5c-117">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-117">String</span></span>|  
|<span data-ttu-id="f3b5c-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f3b5c-118">TABLE_SCHEM</span></span>|<span data-ttu-id="f3b5c-119">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-119">String</span></span>|  
|<span data-ttu-id="f3b5c-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-120">TABLE_NAME</span></span>|<span data-ttu-id="f3b5c-121">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-121">String</span></span>|  
|<span data-ttu-id="f3b5c-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-122">TABLE_TYPE</span></span>|<span data-ttu-id="f3b5c-123">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-123">String</span></span>|  
|<span data-ttu-id="f3b5c-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-124">REMARKS</span></span>|<span data-ttu-id="f3b5c-125">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="f3b5c-126">Indexes</span><span class="sxs-lookup"><span data-stu-id="f3b5c-126">Indexes</span></span>  
  
|<span data-ttu-id="f3b5c-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f3b5c-127">ColumnName</span></span>|<span data-ttu-id="f3b5c-128">DataType</span><span class="sxs-lookup"><span data-stu-id="f3b5c-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f3b5c-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="f3b5c-129">TABLE_CAT</span></span>|<span data-ttu-id="f3b5c-130">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-130">String</span></span>|  
|<span data-ttu-id="f3b5c-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f3b5c-131">TABLE_SCHEM</span></span>|<span data-ttu-id="f3b5c-132">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-132">String</span></span>|  
|<span data-ttu-id="f3b5c-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-133">TABLE_NAME</span></span>|<span data-ttu-id="f3b5c-134">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-134">String</span></span>|  
|<span data-ttu-id="f3b5c-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-135">NON_UNIQUE</span></span>|<span data-ttu-id="f3b5c-136">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-136">Int16</span></span>|  
|<span data-ttu-id="f3b5c-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f3b5c-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="f3b5c-138">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-138">String</span></span>|  
|<span data-ttu-id="f3b5c-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-139">INDEX_NAME</span></span>|<span data-ttu-id="f3b5c-140">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-140">String</span></span>|  
|<span data-ttu-id="f3b5c-141">TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-141">TYPE</span></span>|<span data-ttu-id="f3b5c-142">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-142">Int16</span></span>|  
|<span data-ttu-id="f3b5c-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f3b5c-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="f3b5c-144">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-144">Int16</span></span>|  
|<span data-ttu-id="f3b5c-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-145">COLUMN_NAME</span></span>|<span data-ttu-id="f3b5c-146">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-146">String</span></span>|  
|<span data-ttu-id="f3b5c-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="f3b5c-147">ASC_OR_DESC</span></span>|<span data-ttu-id="f3b5c-148">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-148">String</span></span>|  
|<span data-ttu-id="f3b5c-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="f3b5c-149">CARDINATLITY</span></span>|<span data-ttu-id="f3b5c-150">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-150">Int32</span></span>|  
|<span data-ttu-id="f3b5c-151">PAGES</span><span class="sxs-lookup"><span data-stu-id="f3b5c-151">PAGES</span></span>|<span data-ttu-id="f3b5c-152">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-152">Int32</span></span>|  
|<span data-ttu-id="f3b5c-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="f3b5c-153">FILTER_CONDITION</span></span>|<span data-ttu-id="f3b5c-154">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-154">String</span></span>|  
|<span data-ttu-id="f3b5c-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f3b5c-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="f3b5c-156">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-156">String</span></span>|  
|<span data-ttu-id="f3b5c-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="f3b5c-158">Byte</span><span class="sxs-lookup"><span data-stu-id="f3b5c-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="f3b5c-159">列</span><span class="sxs-lookup"><span data-stu-id="f3b5c-159">Columns</span></span>  
  
|<span data-ttu-id="f3b5c-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f3b5c-160">ColumnName</span></span>|<span data-ttu-id="f3b5c-161">DataType</span><span class="sxs-lookup"><span data-stu-id="f3b5c-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f3b5c-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="f3b5c-162">TABLE_CAT</span></span>|<span data-ttu-id="f3b5c-163">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-163">String</span></span>|  
|<span data-ttu-id="f3b5c-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f3b5c-164">TABLE_SCHEM</span></span>|<span data-ttu-id="f3b5c-165">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-165">String</span></span>|  
|<span data-ttu-id="f3b5c-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-166">TABLE_NAME</span></span>|<span data-ttu-id="f3b5c-167">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-167">String</span></span>|  
|<span data-ttu-id="f3b5c-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-168">COLUMN_NAME</span></span>|<span data-ttu-id="f3b5c-169">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-169">String</span></span>|  
|<span data-ttu-id="f3b5c-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-170">DATA_TYPE</span></span>|<span data-ttu-id="f3b5c-171">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-171">Int16</span></span>|  
|<span data-ttu-id="f3b5c-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-172">TYPE_NAME</span></span>|<span data-ttu-id="f3b5c-173">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-173">String</span></span>|  
|<span data-ttu-id="f3b5c-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-174">COLUMN_SIZE</span></span>|<span data-ttu-id="f3b5c-175">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-175">Int32</span></span>|  
|<span data-ttu-id="f3b5c-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f3b5c-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="f3b5c-177">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-177">Int32</span></span>|  
|<span data-ttu-id="f3b5c-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="f3b5c-179">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-179">Int16</span></span>|  
|<span data-ttu-id="f3b5c-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="f3b5c-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="f3b5c-181">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-181">Int16</span></span>|  
|<span data-ttu-id="f3b5c-182">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-182">NULLABLE</span></span>|<span data-ttu-id="f3b5c-183">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-183">Int16</span></span>|  
|<span data-ttu-id="f3b5c-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-184">REMARKS</span></span>|<span data-ttu-id="f3b5c-185">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-185">String</span></span>|  
|<span data-ttu-id="f3b5c-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="f3b5c-186">COLUMN_DEF</span></span>|<span data-ttu-id="f3b5c-187">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-187">String</span></span>|  
|<span data-ttu-id="f3b5c-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="f3b5c-189">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-189">Int16</span></span>|  
|<span data-ttu-id="f3b5c-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="f3b5c-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="f3b5c-191">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-191">Int16</span></span>|  
|<span data-ttu-id="f3b5c-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f3b5c-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="f3b5c-193">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-193">Int32</span></span>|  
|<span data-ttu-id="f3b5c-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f3b5c-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="f3b5c-195">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-195">Int32</span></span>|  
|<span data-ttu-id="f3b5c-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-196">IS_NULLABLE</span></span>|<span data-ttu-id="f3b5c-197">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-197">String</span></span>|  
|<span data-ttu-id="f3b5c-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f3b5c-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="f3b5c-199">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-199">String</span></span>|  
|<span data-ttu-id="f3b5c-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f3b5c-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="f3b5c-201">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-201">String</span></span>|  
|<span data-ttu-id="f3b5c-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="f3b5c-203">Byte</span><span class="sxs-lookup"><span data-stu-id="f3b5c-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="f3b5c-204">手順</span><span class="sxs-lookup"><span data-stu-id="f3b5c-204">Procedures</span></span>  
  
|<span data-ttu-id="f3b5c-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f3b5c-205">ColumnName</span></span>|<span data-ttu-id="f3b5c-206">DataType</span><span class="sxs-lookup"><span data-stu-id="f3b5c-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f3b5c-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="f3b5c-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="f3b5c-208">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-208">String</span></span>|  
|<span data-ttu-id="f3b5c-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f3b5c-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="f3b5c-210">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-210">String</span></span>|  
|<span data-ttu-id="f3b5c-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="f3b5c-212">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-212">String</span></span>|  
|<span data-ttu-id="f3b5c-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="f3b5c-214">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-214">Int32</span></span>|  
|<span data-ttu-id="f3b5c-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="f3b5c-216">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-216">Int32</span></span>|  
|<span data-ttu-id="f3b5c-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="f3b5c-218">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-218">Int32</span></span>|  
|<span data-ttu-id="f3b5c-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-219">REMARKS</span></span>|<span data-ttu-id="f3b5c-220">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-220">String</span></span>|  
|<span data-ttu-id="f3b5c-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="f3b5c-222">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="f3b5c-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f3b5c-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="f3b5c-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f3b5c-224">ColumnName</span></span>|<span data-ttu-id="f3b5c-225">DataType</span><span class="sxs-lookup"><span data-stu-id="f3b5c-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f3b5c-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="f3b5c-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="f3b5c-227">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-227">String</span></span>|  
|<span data-ttu-id="f3b5c-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f3b5c-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="f3b5c-229">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-229">String</span></span>|  
|<span data-ttu-id="f3b5c-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="f3b5c-231">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-231">String</span></span>|  
|<span data-ttu-id="f3b5c-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-232">COLUMN_NAME</span></span>|<span data-ttu-id="f3b5c-233">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-233">String</span></span>|  
|<span data-ttu-id="f3b5c-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-234">COLUMN_TYPE</span></span>|<span data-ttu-id="f3b5c-235">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-235">Int16</span></span>|  
|<span data-ttu-id="f3b5c-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-236">DATA_TYPE</span></span>|<span data-ttu-id="f3b5c-237">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-237">Int16</span></span>|  
|<span data-ttu-id="f3b5c-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-238">TYPE_NAME</span></span>|<span data-ttu-id="f3b5c-239">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-239">String</span></span>|  
|<span data-ttu-id="f3b5c-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-240">COLUMN_SIZE</span></span>|<span data-ttu-id="f3b5c-241">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-241">Int32</span></span>|  
|<span data-ttu-id="f3b5c-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f3b5c-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="f3b5c-243">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-243">Int32</span></span>|  
|<span data-ttu-id="f3b5c-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="f3b5c-245">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-245">Int16</span></span>|  
|<span data-ttu-id="f3b5c-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="f3b5c-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="f3b5c-247">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-247">Int16</span></span>|  
|<span data-ttu-id="f3b5c-248">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-248">NULLABLE</span></span>|<span data-ttu-id="f3b5c-249">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-249">Int16</span></span>|  
|<span data-ttu-id="f3b5c-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-250">REMARKS</span></span>|<span data-ttu-id="f3b5c-251">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-251">String</span></span>|  
|<span data-ttu-id="f3b5c-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="f3b5c-252">COLUMN_DEF</span></span>|<span data-ttu-id="f3b5c-253">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-253">String</span></span>|  
|<span data-ttu-id="f3b5c-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="f3b5c-255">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-255">Int16</span></span>|  
|<span data-ttu-id="f3b5c-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="f3b5c-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="f3b5c-257">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-257">Int16</span></span>|  
|<span data-ttu-id="f3b5c-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f3b5c-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="f3b5c-259">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-259">Int32</span></span>|  
|<span data-ttu-id="f3b5c-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f3b5c-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="f3b5c-261">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-261">Int32</span></span>|  
|<span data-ttu-id="f3b5c-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-262">IS_NULLABLE</span></span>|<span data-ttu-id="f3b5c-263">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-263">String</span></span>|  
|<span data-ttu-id="f3b5c-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f3b5c-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="f3b5c-265">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-265">String</span></span>|  
|<span data-ttu-id="f3b5c-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f3b5c-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="f3b5c-267">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-267">String</span></span>|  
|<span data-ttu-id="f3b5c-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="f3b5c-269">Byte</span><span class="sxs-lookup"><span data-stu-id="f3b5c-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="f3b5c-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f3b5c-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="f3b5c-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f3b5c-271">ColumnName</span></span>|<span data-ttu-id="f3b5c-272">DataType</span><span class="sxs-lookup"><span data-stu-id="f3b5c-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f3b5c-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="f3b5c-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="f3b5c-274">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-274">String</span></span>|  
|<span data-ttu-id="f3b5c-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f3b5c-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="f3b5c-276">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-276">String</span></span>|  
|<span data-ttu-id="f3b5c-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="f3b5c-278">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-278">String</span></span>|  
|<span data-ttu-id="f3b5c-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-279">COLUMN_NAME</span></span>|<span data-ttu-id="f3b5c-280">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-280">String</span></span>|  
|<span data-ttu-id="f3b5c-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-281">COLUMN_TYPE</span></span>|<span data-ttu-id="f3b5c-282">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-282">Int16</span></span>|  
|<span data-ttu-id="f3b5c-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-283">DATA_TYPE</span></span>|<span data-ttu-id="f3b5c-284">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-284">Int16</span></span>|  
|<span data-ttu-id="f3b5c-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-285">TYPE_NAME</span></span>|<span data-ttu-id="f3b5c-286">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-286">String</span></span>|  
|<span data-ttu-id="f3b5c-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-287">COLUMN_SIZE</span></span>|<span data-ttu-id="f3b5c-288">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-288">Int32</span></span>|  
|<span data-ttu-id="f3b5c-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f3b5c-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="f3b5c-290">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-290">Int32</span></span>|  
|<span data-ttu-id="f3b5c-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="f3b5c-292">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-292">Int16</span></span>|  
|<span data-ttu-id="f3b5c-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="f3b5c-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="f3b5c-294">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-294">Int16</span></span>|  
|<span data-ttu-id="f3b5c-295">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-295">NULLABLE</span></span>|<span data-ttu-id="f3b5c-296">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-296">Int16</span></span>|  
|<span data-ttu-id="f3b5c-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-297">REMARKS</span></span>|<span data-ttu-id="f3b5c-298">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-298">String</span></span>|  
|<span data-ttu-id="f3b5c-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="f3b5c-299">COLUMN_DEF</span></span>|<span data-ttu-id="f3b5c-300">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-300">String</span></span>|  
|<span data-ttu-id="f3b5c-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="f3b5c-302">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-302">Int16</span></span>|  
|<span data-ttu-id="f3b5c-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="f3b5c-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="f3b5c-304">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-304">Int16</span></span>|  
|<span data-ttu-id="f3b5c-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f3b5c-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="f3b5c-306">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-306">Int32</span></span>|  
|<span data-ttu-id="f3b5c-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f3b5c-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="f3b5c-308">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-308">Int32</span></span>|  
|<span data-ttu-id="f3b5c-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-309">IS_NULLABLE</span></span>|<span data-ttu-id="f3b5c-310">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-310">String</span></span>|  
|<span data-ttu-id="f3b5c-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f3b5c-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="f3b5c-312">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-312">String</span></span>|  
|<span data-ttu-id="f3b5c-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f3b5c-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="f3b5c-314">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-314">String</span></span>|  
|<span data-ttu-id="f3b5c-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="f3b5c-316">Byte</span><span class="sxs-lookup"><span data-stu-id="f3b5c-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="f3b5c-317">Microsoft Oracle ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="f3b5c-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="f3b5c-318">Microsoft SQL Server Oracle ODBC Driver は、共通のスキーマ コレクションに加えて次の特定のスキーマ コレクションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="f3b5c-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="f3b5c-319">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="f3b5c-319">Tables</span></span>  
  
-   <span data-ttu-id="f3b5c-320">列</span><span class="sxs-lookup"><span data-stu-id="f3b5c-320">Columns</span></span>  
  
-   <span data-ttu-id="f3b5c-321">手順</span><span class="sxs-lookup"><span data-stu-id="f3b5c-321">Procedures</span></span>  
  
-   <span data-ttu-id="f3b5c-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f3b5c-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="f3b5c-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f3b5c-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="f3b5c-324">ビュー</span><span class="sxs-lookup"><span data-stu-id="f3b5c-324">Views</span></span>  
  
-   <span data-ttu-id="f3b5c-325">Indexes</span><span class="sxs-lookup"><span data-stu-id="f3b5c-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="f3b5c-326">Tables と Views</span><span class="sxs-lookup"><span data-stu-id="f3b5c-326">Tables and Views</span></span>  
  
|<span data-ttu-id="f3b5c-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f3b5c-327">ColumnName</span></span>|<span data-ttu-id="f3b5c-328">DataType</span><span class="sxs-lookup"><span data-stu-id="f3b5c-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f3b5c-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f3b5c-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="f3b5c-330">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-330">String</span></span>|  
|<span data-ttu-id="f3b5c-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f3b5c-331">TABLE_OWNER</span></span>|<span data-ttu-id="f3b5c-332">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-332">String</span></span>|  
|<span data-ttu-id="f3b5c-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-333">TABLE_NAME</span></span>|<span data-ttu-id="f3b5c-334">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-334">String</span></span>|  
|<span data-ttu-id="f3b5c-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-335">TABLE_TYPE</span></span>|<span data-ttu-id="f3b5c-336">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-336">String</span></span>|  
|<span data-ttu-id="f3b5c-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-337">REMARKS</span></span>|<span data-ttu-id="f3b5c-338">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="f3b5c-339">列</span><span class="sxs-lookup"><span data-stu-id="f3b5c-339">Columns</span></span>  
  
|<span data-ttu-id="f3b5c-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f3b5c-340">ColumnName</span></span>|<span data-ttu-id="f3b5c-341">DataType</span><span class="sxs-lookup"><span data-stu-id="f3b5c-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f3b5c-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f3b5c-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="f3b5c-343">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-343">String</span></span>|  
|<span data-ttu-id="f3b5c-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f3b5c-344">TABLE_OWNER</span></span>|<span data-ttu-id="f3b5c-345">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-345">String</span></span>|  
|<span data-ttu-id="f3b5c-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-346">TABLE_NAME</span></span>|<span data-ttu-id="f3b5c-347">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-347">String</span></span>|  
|<span data-ttu-id="f3b5c-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-348">COLUMN_NAME</span></span>|<span data-ttu-id="f3b5c-349">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-349">String</span></span>|  
|<span data-ttu-id="f3b5c-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-350">DATA_TYPE</span></span>|<span data-ttu-id="f3b5c-351">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-351">Int16</span></span>|  
|<span data-ttu-id="f3b5c-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-352">TYPE_NAME</span></span>|<span data-ttu-id="f3b5c-353">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-353">String</span></span>|  
|<span data-ttu-id="f3b5c-354">PRECISION</span><span class="sxs-lookup"><span data-stu-id="f3b5c-354">PRECISION</span></span>|<span data-ttu-id="f3b5c-355">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-355">Int32</span></span>|  
|<span data-ttu-id="f3b5c-356">LENGTH</span><span class="sxs-lookup"><span data-stu-id="f3b5c-356">LENGTH</span></span>|<span data-ttu-id="f3b5c-357">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-357">Int32</span></span>|  
|<span data-ttu-id="f3b5c-358">SCALE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-358">SCALE</span></span>|<span data-ttu-id="f3b5c-359">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-359">Int16</span></span>|  
|<span data-ttu-id="f3b5c-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="f3b5c-360">RADIX</span></span>|<span data-ttu-id="f3b5c-361">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-361">Int16</span></span>|  
|<span data-ttu-id="f3b5c-362">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-362">NULLABLE</span></span>|<span data-ttu-id="f3b5c-363">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-363">Int16</span></span>|  
|<span data-ttu-id="f3b5c-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-364">REMARKS</span></span>|<span data-ttu-id="f3b5c-365">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-365">String</span></span>|  
|<span data-ttu-id="f3b5c-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f3b5c-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="f3b5c-367">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="f3b5c-368">手順</span><span class="sxs-lookup"><span data-stu-id="f3b5c-368">Procedures</span></span>  
  
|<span data-ttu-id="f3b5c-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f3b5c-369">ColumnName</span></span>|<span data-ttu-id="f3b5c-370">DataType</span><span class="sxs-lookup"><span data-stu-id="f3b5c-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f3b5c-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f3b5c-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="f3b5c-372">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-372">String</span></span>|  
|<span data-ttu-id="f3b5c-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f3b5c-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="f3b5c-374">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-374">String</span></span>|  
|<span data-ttu-id="f3b5c-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="f3b5c-376">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-376">String</span></span>|  
|<span data-ttu-id="f3b5c-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="f3b5c-378">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-378">Int16</span></span>|  
|<span data-ttu-id="f3b5c-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="f3b5c-380">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-380">Int16</span></span>|  
|<span data-ttu-id="f3b5c-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="f3b5c-382">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-382">Int16</span></span>|  
|<span data-ttu-id="f3b5c-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-383">REMARKS</span></span>|<span data-ttu-id="f3b5c-384">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-384">String</span></span>|  
|<span data-ttu-id="f3b5c-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="f3b5c-386">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="f3b5c-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f3b5c-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="f3b5c-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f3b5c-388">ColumnName</span></span>|<span data-ttu-id="f3b5c-389">DataType</span><span class="sxs-lookup"><span data-stu-id="f3b5c-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f3b5c-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f3b5c-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="f3b5c-391">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-391">String</span></span>|  
|<span data-ttu-id="f3b5c-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f3b5c-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="f3b5c-393">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-393">String</span></span>|  
|<span data-ttu-id="f3b5c-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="f3b5c-395">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-395">String</span></span>|  
|<span data-ttu-id="f3b5c-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-396">COLUMN_NAME</span></span>|<span data-ttu-id="f3b5c-397">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-397">String</span></span>|  
|<span data-ttu-id="f3b5c-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-398">COLUMN_TYPE</span></span>|<span data-ttu-id="f3b5c-399">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-399">Int16</span></span>|  
|<span data-ttu-id="f3b5c-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-400">DATA_TYPE</span></span>|<span data-ttu-id="f3b5c-401">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-401">Int16</span></span>|  
|<span data-ttu-id="f3b5c-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-402">TYPE_NAME</span></span>|<span data-ttu-id="f3b5c-403">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-403">String</span></span>|  
|<span data-ttu-id="f3b5c-404">PRECISION</span><span class="sxs-lookup"><span data-stu-id="f3b5c-404">PRECISION</span></span>|<span data-ttu-id="f3b5c-405">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-405">Int32</span></span>|  
|<span data-ttu-id="f3b5c-406">LENGTH</span><span class="sxs-lookup"><span data-stu-id="f3b5c-406">LENGTH</span></span>|<span data-ttu-id="f3b5c-407">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-407">Int32</span></span>|  
|<span data-ttu-id="f3b5c-408">SCALE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-408">SCALE</span></span>|<span data-ttu-id="f3b5c-409">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-409">Int16</span></span>|  
|<span data-ttu-id="f3b5c-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="f3b5c-410">RADIX</span></span>|<span data-ttu-id="f3b5c-411">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-411">Int16</span></span>|  
|<span data-ttu-id="f3b5c-412">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-412">NULLABLE</span></span>|<span data-ttu-id="f3b5c-413">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-413">Int16</span></span>|  
|<span data-ttu-id="f3b5c-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-414">REMARKS</span></span>|<span data-ttu-id="f3b5c-415">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-415">String</span></span>|  
|<span data-ttu-id="f3b5c-416">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="f3b5c-416">OVERLOAD</span></span>|<span data-ttu-id="f3b5c-417">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-417">Int32</span></span>|  
|<span data-ttu-id="f3b5c-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f3b5c-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="f3b5c-419">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="f3b5c-420">Microsoft Jet ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="f3b5c-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="f3b5c-421">Microsoft Jet ODBC Driver は、共通のスキーマ コレクションに加えて次のスキーマ コレクションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f3b5c-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="f3b5c-422">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="f3b5c-422">Tables</span></span>  
  
-   <span data-ttu-id="f3b5c-423">Indexes</span><span class="sxs-lookup"><span data-stu-id="f3b5c-423">Indexes</span></span>  
  
-   <span data-ttu-id="f3b5c-424">列</span><span class="sxs-lookup"><span data-stu-id="f3b5c-424">Columns</span></span>  
  
-   <span data-ttu-id="f3b5c-425">手順</span><span class="sxs-lookup"><span data-stu-id="f3b5c-425">Procedures</span></span>  
  
-   <span data-ttu-id="f3b5c-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f3b5c-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="f3b5c-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f3b5c-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="f3b5c-428">ビュー</span><span class="sxs-lookup"><span data-stu-id="f3b5c-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="f3b5c-429">Tables と Views</span><span class="sxs-lookup"><span data-stu-id="f3b5c-429">Tables and Views</span></span>  
  
|<span data-ttu-id="f3b5c-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f3b5c-430">ColumnName</span></span>|<span data-ttu-id="f3b5c-431">DataType</span><span class="sxs-lookup"><span data-stu-id="f3b5c-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f3b5c-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f3b5c-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="f3b5c-433">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-433">String</span></span>|  
|<span data-ttu-id="f3b5c-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f3b5c-434">TABLE_OWNER</span></span>|<span data-ttu-id="f3b5c-435">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-435">String</span></span>|  
|<span data-ttu-id="f3b5c-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-436">TABLE_NAME</span></span>|<span data-ttu-id="f3b5c-437">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-437">String</span></span>|  
|<span data-ttu-id="f3b5c-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-438">TABLE_TYPE</span></span>|<span data-ttu-id="f3b5c-439">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-439">String</span></span>|  
|<span data-ttu-id="f3b5c-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-440">REMARKS</span></span>|<span data-ttu-id="f3b5c-441">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="f3b5c-442">列</span><span class="sxs-lookup"><span data-stu-id="f3b5c-442">Columns</span></span>  
  
|<span data-ttu-id="f3b5c-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f3b5c-443">ColumnName</span></span>|<span data-ttu-id="f3b5c-444">DataType</span><span class="sxs-lookup"><span data-stu-id="f3b5c-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f3b5c-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f3b5c-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="f3b5c-446">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-446">String</span></span>|  
|<span data-ttu-id="f3b5c-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f3b5c-447">TABLE_OWNER</span></span>|<span data-ttu-id="f3b5c-448">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-448">String</span></span>|  
|<span data-ttu-id="f3b5c-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-449">TABLE_NAME</span></span>|<span data-ttu-id="f3b5c-450">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-450">String</span></span>|  
|<span data-ttu-id="f3b5c-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-451">COLUMN_NAME</span></span>|<span data-ttu-id="f3b5c-452">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-452">String</span></span>|  
|<span data-ttu-id="f3b5c-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-453">DATA_TYPE</span></span>|<span data-ttu-id="f3b5c-454">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-454">Int16</span></span>|  
|<span data-ttu-id="f3b5c-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-455">TYPE_NAME</span></span>|<span data-ttu-id="f3b5c-456">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-456">String</span></span>|  
|<span data-ttu-id="f3b5c-457">PRECISION</span><span class="sxs-lookup"><span data-stu-id="f3b5c-457">PRECISION</span></span>|<span data-ttu-id="f3b5c-458">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-458">Int32</span></span>|  
|<span data-ttu-id="f3b5c-459">LENGTH</span><span class="sxs-lookup"><span data-stu-id="f3b5c-459">LENGTH</span></span>|<span data-ttu-id="f3b5c-460">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-460">Int32</span></span>|  
|<span data-ttu-id="f3b5c-461">SCALE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-461">SCALE</span></span>|<span data-ttu-id="f3b5c-462">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-462">Int16</span></span>|  
|<span data-ttu-id="f3b5c-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="f3b5c-463">RADIX</span></span>|<span data-ttu-id="f3b5c-464">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-464">Int16</span></span>|  
|<span data-ttu-id="f3b5c-465">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-465">NULLABLE</span></span>|<span data-ttu-id="f3b5c-466">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-466">Int16</span></span>|  
|<span data-ttu-id="f3b5c-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-467">REMARKS</span></span>|<span data-ttu-id="f3b5c-468">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-468">String</span></span>|  
|<span data-ttu-id="f3b5c-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f3b5c-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="f3b5c-470">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="f3b5c-471">手順</span><span class="sxs-lookup"><span data-stu-id="f3b5c-471">Procedures</span></span>  
  
|<span data-ttu-id="f3b5c-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f3b5c-472">ColumnName</span></span>|<span data-ttu-id="f3b5c-473">DataType</span><span class="sxs-lookup"><span data-stu-id="f3b5c-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f3b5c-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f3b5c-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="f3b5c-475">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-475">String</span></span>|  
|<span data-ttu-id="f3b5c-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f3b5c-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="f3b5c-477">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-477">String</span></span>|  
|<span data-ttu-id="f3b5c-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="f3b5c-479">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-479">String</span></span>|  
|<span data-ttu-id="f3b5c-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="f3b5c-481">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-481">Int16</span></span>|  
|<span data-ttu-id="f3b5c-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="f3b5c-483">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-483">Int16</span></span>|  
|<span data-ttu-id="f3b5c-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="f3b5c-485">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-485">Int16</span></span>|  
|<span data-ttu-id="f3b5c-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-486">REMARKS</span></span>|<span data-ttu-id="f3b5c-487">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-487">String</span></span>|  
|<span data-ttu-id="f3b5c-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="f3b5c-489">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="f3b5c-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f3b5c-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="f3b5c-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f3b5c-491">ColumnName</span></span>|<span data-ttu-id="f3b5c-492">DataType</span><span class="sxs-lookup"><span data-stu-id="f3b5c-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f3b5c-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f3b5c-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="f3b5c-494">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-494">String</span></span>|  
|<span data-ttu-id="f3b5c-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f3b5c-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="f3b5c-496">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-496">String</span></span>|  
|<span data-ttu-id="f3b5c-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="f3b5c-498">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-498">String</span></span>|  
|<span data-ttu-id="f3b5c-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-499">COLUMN_NAME</span></span>|<span data-ttu-id="f3b5c-500">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-500">String</span></span>|  
|<span data-ttu-id="f3b5c-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-501">COLUMN_TYPE</span></span>|<span data-ttu-id="f3b5c-502">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-502">Int16</span></span>|  
|<span data-ttu-id="f3b5c-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-503">DATA_TYPE</span></span>|<span data-ttu-id="f3b5c-504">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-504">Int16</span></span>|  
|<span data-ttu-id="f3b5c-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-505">TYPE_NAME</span></span>|<span data-ttu-id="f3b5c-506">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-506">String</span></span>|  
|<span data-ttu-id="f3b5c-507">PRECISION</span><span class="sxs-lookup"><span data-stu-id="f3b5c-507">PRECISION</span></span>|<span data-ttu-id="f3b5c-508">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-508">Int32</span></span>|  
|<span data-ttu-id="f3b5c-509">LENGTH</span><span class="sxs-lookup"><span data-stu-id="f3b5c-509">LENGTH</span></span>|<span data-ttu-id="f3b5c-510">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-510">Int32</span></span>|  
|<span data-ttu-id="f3b5c-511">SCALE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-511">SCALE</span></span>|<span data-ttu-id="f3b5c-512">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-512">Int16</span></span>|  
|<span data-ttu-id="f3b5c-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="f3b5c-513">RADIX</span></span>|<span data-ttu-id="f3b5c-514">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-514">Int16</span></span>|  
|<span data-ttu-id="f3b5c-515">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-515">NULLABLE</span></span>|<span data-ttu-id="f3b5c-516">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-516">Int16</span></span>|  
|<span data-ttu-id="f3b5c-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-517">REMARKS</span></span>|<span data-ttu-id="f3b5c-518">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-518">String</span></span>|  
|<span data-ttu-id="f3b5c-519">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="f3b5c-519">OVERLOAD</span></span>|<span data-ttu-id="f3b5c-520">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-520">Int32</span></span>|  
|<span data-ttu-id="f3b5c-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f3b5c-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="f3b5c-522">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="f3b5c-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f3b5c-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="f3b5c-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f3b5c-524">ColumnName</span></span>|<span data-ttu-id="f3b5c-525">DataType</span><span class="sxs-lookup"><span data-stu-id="f3b5c-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f3b5c-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="f3b5c-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="f3b5c-527">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-527">String</span></span>|  
|<span data-ttu-id="f3b5c-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f3b5c-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="f3b5c-529">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-529">String</span></span>|  
|<span data-ttu-id="f3b5c-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="f3b5c-531">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-531">String</span></span>|  
|<span data-ttu-id="f3b5c-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-532">COLUMN_NAME</span></span>|<span data-ttu-id="f3b5c-533">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-533">String</span></span>|  
|<span data-ttu-id="f3b5c-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-534">COLUMN_TYPE</span></span>|<span data-ttu-id="f3b5c-535">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-535">Int16</span></span>|  
|<span data-ttu-id="f3b5c-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-536">DATA_TYPE</span></span>|<span data-ttu-id="f3b5c-537">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-537">Int16</span></span>|  
|<span data-ttu-id="f3b5c-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f3b5c-538">TYPE_NAME</span></span>|<span data-ttu-id="f3b5c-539">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-539">String</span></span>|  
|<span data-ttu-id="f3b5c-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-540">COLUMN_SIZE</span></span>|<span data-ttu-id="f3b5c-541">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-541">Int32</span></span>|  
|<span data-ttu-id="f3b5c-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f3b5c-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="f3b5c-543">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-543">Int32</span></span>|  
|<span data-ttu-id="f3b5c-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="f3b5c-545">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-545">Int16</span></span>|  
|<span data-ttu-id="f3b5c-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="f3b5c-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="f3b5c-547">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-547">Int16</span></span>|  
|<span data-ttu-id="f3b5c-548">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-548">NULLABLE</span></span>|<span data-ttu-id="f3b5c-549">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-549">Int16</span></span>|  
|<span data-ttu-id="f3b5c-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f3b5c-550">REMARKS</span></span>|<span data-ttu-id="f3b5c-551">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-551">String</span></span>|  
|<span data-ttu-id="f3b5c-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="f3b5c-552">COLUMN_DEF</span></span>|<span data-ttu-id="f3b5c-553">String</span><span class="sxs-lookup"><span data-stu-id="f3b5c-553">String</span></span>|  
|<span data-ttu-id="f3b5c-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="f3b5c-555">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-555">Int16</span></span>|  
|<span data-ttu-id="f3b5c-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="f3b5c-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="f3b5c-557">Int16</span><span class="sxs-lookup"><span data-stu-id="f3b5c-557">Int16</span></span>|  
|<span data-ttu-id="f3b5c-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f3b5c-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="f3b5c-559">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-559">Int32</span></span>|  
|<span data-ttu-id="f3b5c-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f3b5c-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="f3b5c-561">Int32</span><span class="sxs-lookup"><span data-stu-id="f3b5c-561">Int32</span></span>|  
|<span data-ttu-id="f3b5c-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f3b5c-562">IS_NULLABLE</span></span>|<span data-ttu-id="f3b5c-563">文字列型</span><span class="sxs-lookup"><span data-stu-id="f3b5c-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3b5c-564">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3b5c-564">See Also</span></span>  
 [<span data-ttu-id="f3b5c-565">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="f3b5c-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
