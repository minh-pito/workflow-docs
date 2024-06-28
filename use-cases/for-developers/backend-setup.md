# Backend Setup

### Supabase

{% tabs %}
{% tab title="Installing" %}
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

