<template>
  <section class="py-[200px] flex flex-col items-center justify-center px-4">
    <div class="text-[32px] font-semibold text-dark mb-4">Select Companies</div>
    <form class="w-full card">
      <div class="form-group">
        <label class="text-grey">
          Companies
        </label>
        <select class="appearance-none input-field form-icon-chevron-down">
          <option value="" selected>Company Name</option>
        </select>
      </div>
      <a href="/company/1" class="w-full btn btn-primary mt-[14px]">Continue</a>
    </form>
  </section>
</template>

<script>
export default {
}
</script>
