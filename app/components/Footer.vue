<template>
  <footer class="bg-footer text-gray-300">
    <div class="container mx-auto px-6 py-16 grid gap-12 md:grid-cols-2 lg:grid-cols-4">

      <div>
        <h3 class="text-white text-lg font-semibold mb-6">ABOUT US</h3>
        <p class="text-sm leading-relaxed">
          Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
          eiusmod tempor incididunt ut labore et dolore magna.
        </p>

        <button class="mt-4 text-sm text-text hover:underline">
          Read More...
        </button>

        <div class="mt-6 relative">
          <input
            type="email"
            placeholder="Email for Newsletter"
            class="w-full bg-dark text-sm px-4 py-3 rounded focus:outline-none"
          />
          <button
            class="absolute end-3 top-1/2 -translate-y-1/2 text-text"
          >
           <Icon name="bytesize:send"/>
          </button>
        </div>
      </div>
      <div>
        <h3 class="text-white text-lg font-semibold mb-6">NAVIGATION</h3>
        <ul class="space-y-3 text-sm">
          <li><NuxtLink to="/" class="hover:text-white">Home</NuxtLink></li>
          <li><NuxtLink to="/about" class="hover:text-white">About Us</NuxtLink></li>
          <li><NuxtLink to="/blog" class="hover:text-white">Blog</NuxtLink></li>
          <li><NuxtLink to="/services" class="hover:text-white">Our Services</NuxtLink></li>
          <li><NuxtLink to="/contact" class="hover:text-white">Contact Us</NuxtLink></li>
          <li><NuxtLink to="/sitemap" class="hover:text-white">Sitemap</NuxtLink></li>
        </ul>
      </div>

      <div>
        <h3 class="text-white text-lg font-semibold mb-6">OUR SERVICES</h3>
        <ul class="space-y-3 text-sm">
          <li>Land Transport</li>
          <li>Warehousing</li>
          <li>Fast Delivery</li>
          <li>Worldwide Transport</li>
          <li>Sea Freight</li>
          <li>Reliable</li>
        </ul>
      </div>

      <div>
        <h3 class="text-white text-lg font-semibold mb-6">CONTACT US</h3>

        <ul class="space-y-5 text-sm">
          <li class="flex gap-3">
            <Icon name="material-symbols:map-outline-rounded" class="size-7"/>
            <span>
              1234 Sed ut perspiciatis Road,<br />
              At vero eos, D58 8975, London.
            </span>
          </li>

          <li class="flex gap-3">
            <Icon name="fluent:call-20-filled" class="size-7"/>
            <span>
              Toll Free: (123) 4567 8910<br />
              Telephone: (123) 1234 5678
            </span>
          </li>

          <li class="flex gap-3">
            <Icon name="ic:round-email" class="size-7"/>
            <span>
              Email: info@sitename.com<br />
              Web: www.sitename.com
            </span>
          </li>
        </ul>
      </div>

    </div>

    <div class="py-6 bg-dark-footer">
      <div class="container mx-auto px-6 flex flex-col md:flex-row justify-between items-center gap-4 text-sm">
        <p>
          © 2017 Tranship. All Rights Reserved. Template by Softnio.
        </p>

         <ul class="flex justify-between ms-auto md:ms-0 gap-3 ">
      <li>
        <a href="#">
          <Icon name="ri:facebook-fill" class="size-4" />
        </a>
      </li>
      <li>
        <a href="#">
          <Icon name="mdi:twitter" class="size-4" />
        </a>
      </li>
      <li>
        <a href="#">
          <Icon name="basil:linkedin-solid" class="size-4" />
        </a>
      </li>
      <li>
        <a href="#">
          <Icon name="mdi:google-plus" class="size-4" />
        </a>
      </li>
    </ul>
      </div>
    </div>
  </footer>
</template>
