create policy "Enable update for users based on onwer_id"
on "public"."Event"
as PERMISSIVE
for UPDATE
to authenticated
using ( (select auth.uid())::text = "owner_id" )
with check ( (select auth.uid())::text = "owner_id" );
