<!-- eslint-disable vuejs-accessibility/click-events-have-key-events -->
<template>
    <nav class="navbar navbar-light bg-light shadow py-3">
        <div class="container-fluid">
            <span class="navbar-brand mb-0 h1 fs-4">Github Profile Viewer</span>
            <div class="d-flex justify-content-end">
                <button type="button" class="btn btn-primary" @click="$emit('show-home')">
                    View Home
                </button>
            </div>
        </div>
    </nav>
</template>
