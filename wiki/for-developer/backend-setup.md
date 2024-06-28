---
description: Backend documents
---

# Backend Setup

### Supabase

{% tabs %}
{% tab title="Quick start" %}
1. Install supabase cli ([https://supabase.com/docs/guides/cli/getting-started](https://supabase.com/docs/guides/cli/getting-started))
2. `supabase login` -> Enter để login
3. `supabase init` -> tạo ra file config.toml
4. `supabase link` -> chọn project id tương ứng với project -> nhập password của database
5. `supabase start` -> pull các images cần thiết để chạy local

#### Start local function

`supabase functions serve <functions name>` -> start 1 edge function

#### Stop supabase local

`supabase stop` -> stop supabase

#### Deploy local function to remote

1. `supabase functions new <functions name>` -> tạo 1 edge function
2. `supabase functions deploy <functions name>` -> deploy edge function
{% endtab %}

{% tab title="Database" %}
#### Pull database from remote

`supabase db pull --linked`  -> sync database từ remote xuống local

#### Reset database local

`supabase db reset`

#### Dump data remote

`supabase db dump -f supabase/seed.sql --data-only` -> dump data xuống local (run lại lệnh reset sẽ tự động seed vào db local)

#### Generate types from database schema

`supabase gen types typescript --linked`  > functions/shared/supabase.ts
{% endtab %}

{% tab title="Migration" %}
#### Migration list

```bash
supabase migration list        
```

#### Create new migration

```
supabase db pull --linked  -> sync database change từ remote xuống local
or
supabase migration new schema_test
```

#### Apply migration to remote

```
supabase migration up --linked
```
{% endtab %}
{% endtabs %}

***

### Common rules

* PR nào có bất cứ thay đổi trong folder "shared" thì cũng để prefix \[Shared]
* Nếu có env mới, thêm vào env.stage và tạo PR
* PRs mà có Migration thì thêm prefix \[Migration]

***

### **Checklist khi tạo PRs & Merge code:**

* Nếu có thay đổi structure Database thì cần tạo Migration như lúc trước đã trao đổi, thêm prefix \[Migration] vào title của PR
* Nếu có thêm/bớt "Edge Function Secrets" (tạo bằng tay trên Dev supabase) thì cần update vào file "stage.env" và thêm prefix \[Env] vào title của PR
* Nếu có bất kì thay đổi trong folder "shared" thì cần thêm prefix \[Shared] vào title của PR để build lại toàn bộ functions
* Khi tạo PRs cần 2 người khác Review mới được merge Edge Functions cần check kĩ các khai báo files, types,... để Github Actions tự build được lên Staging
* Merge PR vào branch "develop" thì sẽ deploy lên môi trường Staging, còn môi trường Dev thì tụi em tự deploy trong quá trình làm

***

### Checklist setup environment:

**Supabase Realtime: (enable in tables)**

* transactions
* partner-order
